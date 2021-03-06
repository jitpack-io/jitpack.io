Frequently Asked Questions
-

**What happens if a tag is deleted on GitHub?**

If the project was already built JitPack will continue serving the existing artifacts. It will not rebuilt the project at the new tag. 
In case you need to redo a release the best option is to create a new version on GitHub.

**Can I use JitPack with private repositories?**

Yes. See https://jitpack.io/private

**How can I get the latest snapshot of a repository?**

In your build file set the version of your dependency to `-SNAPSHOT`. 
You can also customize how often you want Gradle to check for new snapshots - see [the documentation](https://docs.gradle.org/1.8-rc-1/userguide/dependency_management.html#sec:controlling_caching). 

**Will my builds be reproducible?**

Absolutely. Once JitPack builds a project it keeps the build artifacts (jar, aar, ... files) and continues to serve those for all subsequent requests.

JitPack encourages reproducible builds in general since you need to have a working build file in order to publish artifacts. See also [Reproducible Build](http://martinfowler.com/bliki/ReproducibleBuild.html) article by Martin Fowler.

**Is this like depending on source code repositories in other languages?**

Not really. With JitPack you specify which exact version you want and JitPack builds it. You can't have a dependency on the latest HEAD version. The author of the repository controls when to release a new version using GitHub's releases so from a consumer's perspective it's a typical package repository.

**How are the builds secured?**

Each project is built in its own Docker container and has no access to other builds or files produced by other builds. Containers run only with normal user privileges (no root). All files produced by the build are served over HTTPS (only). 

**Can I rebuilt my project?**

If your first build wasn't successfull you can rebuild it. If you Sign In on JitPack.io then you'll be able to remove the old build and re-requesting it will trigger a new build. 

**Can version ranges be used with JitPack?**

You can use version ranges and Gradle's dynamic versions for releases. Currenly they only resolve to releases that have been built.
`compile 'com.github.User:Repo:1.+'`

**How long can builds take?**

Up to 15 minutes

**Other questions**

Send them to jitpack at jitpack.io or come to https://gitter.im/jitpack
