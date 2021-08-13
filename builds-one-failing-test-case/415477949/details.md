# Information about the failure

| Failure type | Failure details | Failing test case | Changed file by AstorJKali |
|--------------|-----------------|-------------------|----------------------------|
| java.lang.AssertionError | Should have errored out | [ShardManagerTest](https://github.com/repairnator/repairnator-experiments-one-failing-test-case/blob/f7ad5d505ce69c42e153316d445f8a37c1844f97/src/test/java/io/dropwizard/sharding/sharding/ShardManagerTest.java#L43) | [DBShardingBundle](https://github.com/repairnator/repairnator-experiments-one-failing-test-case/blob/f7ad5d505ce69c42e153316d445f8a37c1844f97/src/main/java/io/dropwizard/sharding/DBShardingBundle.java#L121)|

The code-removal patches work because the test case is flaky. Ineed, [Patch 3] only removes a log instruction, without changing the logic of the program, and the program passes all the test cases.
