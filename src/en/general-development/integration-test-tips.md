# Integration Test Tips

This page contains useful tips `Content` integration tests. It is intended to be a resource to help with good practices and finding helper methods unique to integration tests.

If you are looking to start out learning integration tests, check out our tutorial example [Your First Integration Test](../../ss14-by-example/your-first-integration-test.md) before returning here!

## Base Test Classes

All integration tests should derive from one of the pre-existing base test classes. They handle boilerplate code for starting and disposing of tests, set starting conditions and provide a multitude of helper functions.

We currently have the following base test classes:

- `GameTest`

  `GameTest` is a general-purpose test that is meant to work as a base for all types of integration tests.
  It is barebones in that it only sets up the client-server relationship and a few basic system dependencies, but this also keeps it lightweight and modifiable.
  
- `InteractionTest`

  `InteractionTest` is intended to be used for any test involving a player character interacting with other entities.
  By default it spawns a dummy ghost mob with a single hand designated as the "Player", and has additional support for a "Target" entity that is automatically set as the target for the class' test functions.

  Of note, `InteractionTest` is *not* an extension of `GameTest`, which means helper functions between the two tests are not shared.
  
- `MovementTest`

  `MovementTest` is an extension of `InteractionTest` meant to test interactions dependent on traversal.
  It changes the "Player" spawn into a `MobHuman` and adds tiles to the left and right of the test entity.
  In addition the map is given atmospherics and gravity.

## `TestPair` (Content)

`TestPair` is a core class derived from the RobustToolbox class of the same name, initiated for every base test class. It sets up and handles the foundational client-server relationship the game uses to communicate. 

### Setup

- `CreateTestMap`
  
  Sets up a basic testing map consisting of a single tile of plating. Does not feature any gravity or atmospherics.

- `LoadTestMap`
  
  Sets up a test map based on a `ResPath`. Useful if there is a specific environment that needs to be simulated in a test.


## GameTest Helpers

### Server-Client Setup

- `Pair`
  
  `GameTest`'s property for `TestPair`. It is most commonly used with `Pair.CreateTestMap();` at the start of a test to create a map to spawn entities into.

### Test Class 

- `[SidedDependency(Side.Server)] private ISomeManager _sManager = null!;`
  
  Preferred dependency injection format for any manager/system included in test classes. Supports `Side.Server` and `Side.Client`; for most testcases, you are likely to be using the server-sided dependency.


### Entity Handling

- `SEntMan`, `CEntMan`
  
  Server and client entity managers dependencies. Several helper methods use these for entity handling, but these are available as shorthands if you need to use anything that isn't a helper.

- `SComp`, `CComp`, `STryComp`, `CTryComp`
  
  Server and client component resolution methods using the corresponding entity manager.

- `SSpawn`, `CSpawn`, `SSpawnPosition`, `CSpawnPosition`
  
  Server and client spawn methods, that also track the entities for post-test clean-up.

- `async Task<EntityUid> Spawn`, `async Task<EntityUid> SpawnAtPosition`
  
  Server-side spawn methods (`SSpawn`, `SSpawnPosition`) that are run asynchronously.

- `SDeleteNow`, `CDeleteNow`, `SQueueDel`, `CQueueDel`
  
  Server and client deletion/queued deletion methods.

