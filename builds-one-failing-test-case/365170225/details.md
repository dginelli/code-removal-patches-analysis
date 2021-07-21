# Information about the failure

| Failure type | Failing test case | Changed file by jKali |
|--------------|-------------------|----------------------------|
| java.lang.AssertionError | [DefaultClusterServiceTest.java](https://github.com/repairnator/repairnator-experiments-jkali-one-failing-test-case/blob/0d0ebd0dc2bb7f81967c94e3471208eb9cdeacf7/cluster/src/test/java/io/atomix/cluster/impl/DefaultClusterServiceTest.java#L195) | [DefaultClusterService.java](https://github.com/repa


- **Failing Travis CI Build**: [https://api.travis-ci.org/v3/build/365170225](https://api.travis-ci.org/v3/build/365170225)
- **Passing Travis CI Build**: Not found, because there are many builds after the failing one, and none of them pass.
- **List of Builds**: [https://api.travis-ci.org/v3/repo/atomix/1833868/builds?offset=1500](https://api.travis-ci.org/v3/repo/atomix/1833868/builds?offset=1500)
- **Next passed Build**: [https://api.travis-ci.org/v3/build/365716340](https://api.travis-ci.org/v3/build/365716340)

The build was failing also before this one.

irnator/repairnator-experiments-jkali-one-failing-test-case/blob/0d0ebd0dc2bb7f81967c94e3471208eb9cdeacf7/cluster/src/main/java/io/atomix/cluster/impl/DefaultClusterService.java#L200)|

- **Overview**: The error is related to the status check of a `Node`.

- **Reason why the patch has been generated**: AstorJKali managed to create a patch, because changing the `if condition`, it forced the execution of method `deactivateNode`. This method uses [another way](https://github.com/repairnator/repairnator-experiments-jkali-one-failing-test-case/blob/0d0ebd0dc2bb7f81967c94e3471208eb9cdeacf7/cluster/src/main/java/io/atomix/cluster/impl/DefaultClusterService.java#L289) to get the `node` object (it uses the node id, and it gets the node based on this id, checking in a Map), so that when its status is checked, it is `ACTIVE` (and not `INACTIVE`), and thus the method `deactivate(Node)` is executed full. In this way, the node is deactivated and the assertion is satisfied.

- **Useful information for the developer**: The developer can see how the status of Node is got in the method [`deactivateNode`](https://github.com/repairnator/repairnator-experiments-jkali-one-failing-test-case/blob/0d0ebd0dc2bb7f81967c94e3471208eb9cdeacf7/cluster/src/main/java/io/atomix/cluster/impl/DefaultClusterService.java#L288), and use the same way to check the status in the `if condition` changed by AstorJKali. Indeed, in this way, all the test cases pass.

- **Possible fix**:

```diff
- if (node.getState() == State.ACTIVE) {
+ if (this.nodes.get(node.id()).getState() == State.ACTIVE)
```

**Pull Request History**: [https://github.com/atomix/atomix/pull/484/](https://github.com/atomix/atomix/pull/484/)
