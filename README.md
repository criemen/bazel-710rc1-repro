Reproduces the crash

FATAL: bazel crashed due to an internal error. Printing stack trace:
java.lang.RuntimeException: Unrecoverable error while evaluating node 'REPOSITORY_DIRECTORY:@@rules_nodejs~~node~nodejs' (requested by nodes 'PACKAGE_LOOKUP:@@rules_nodejs~~node~nodejs//')
        at com.google.devtools.build.skyframe.AbstractParallelEvaluator$Evaluate.run(AbstractParallelEvaluator.java:550)
        at com.google.devtools.build.lib.concurrent.AbstractQueueVisitor$WrappedRunnable.run(AbstractQueueVisitor.java:414)
        at java.base/java.util.concurrent.ForkJoinTask$RunnableExecuteAction.exec(Unknown Source)
        at java.base/java.util.concurrent.ForkJoinTask.doExec(Unknown Source)
        at java.base/java.util.concurrent.ForkJoinPool$WorkQueue.topLevelExec(Unknown Source)
        at java.base/java.util.concurrent.ForkJoinPool.scan(Unknown Source)
        at java.base/java.util.concurrent.ForkJoinPool.runWorker(Unknown Source)
        at java.base/java.util.concurrent.ForkJoinWorkerThread.run(Unknown Source)
Caused by: java.lang.NullPointerException
        at com.google.common.base.Preconditions.checkNotNull(Preconditions.java:903)
        at com.google.devtools.build.lib.rules.repository.RepositoryDelegatorFunction.fetchRepository(RepositoryDelegatorFunction.java:439)
        at com.google.devtools.build.lib.rules.repository.RepositoryDelegatorFunction.compute(RepositoryDelegatorFunction.java:205)
        at com.google.devtools.build.skyframe.AbstractParallelEvaluator$Evaluate.run(AbstractParallelEvaluator.java:461)
        ... 7 more

with bazel 7.1.0rc1.

Trigger with `bazelisk build //:typescript`.
