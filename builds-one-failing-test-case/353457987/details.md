# Information about the failure

| Failure type | Failure details | Failing test case | Changed file by AstorJKali |
|--------------|-------------------|----------------------------|---------------------|
| org.mockito.exceptions.verification.TooLittleActualInvocations | processor.process("k1"); Wanted 2 times:-> at io.enmasse.k8s.api.cache.FifoQueueTest.testRemove(FifoQueueTest.java:64) But was 1 time: -> at io.enmasse.k8s.api.cache.FifoQueue.pop(FifoQueue.java:65)|[FifoQueueTest.java](https://github.com/repairnator/repairnator-experiments-jkali-one-failing-test-case/blob/733c76e58890cea2d4ce004760de719ae04ca826/k8s-api/src/test/java/io/enmasse/k8s/api/cache/FifoQueueTest.java#L64) | [FifoQueue.java](https://github.com/repairnator/repairnator-experiments-jkali-one-failing-test-case/blob/733c76e58890cea2d4ce004760de719ae04ca826/k8s-api/src/main/java/io/enmasse/k8s/api/cache/FifoQueue.java#L54)|
