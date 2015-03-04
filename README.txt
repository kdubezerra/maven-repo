*** to add a jar to this git-based maven repository, run the following with your
    local copy:
    mvn install:install-file -DgroupId=[groupId] -DartifactId=[artifactId]
    -Dversion=[version] -Dpackaging=jar -Dfile=[pathToJar]
    -DlocalRepositoryPath=[pathToGitRepo] -DcreateChecksum=true

[groupId], [artifactId] and [version] can be anything you want, as long as the
    dependency in your project's pom.xml has the same values.
[pathToJar] is the local path to the jar file that you're installing in the
    local copy of the git repository
[pathToGitRepo] is the path of the local copy of the git repository

*** add all files to the git repository and commit to the public remote
    repository

*** in your project's pom.xml you must have the following inside a
    <repositories></repositories> element:

<repository>
    <id>git-[username]</id>
    <name>[username]'s Git based repo</name>
    <url>https://github.com/[username]/[repo-name]/raw/master/</url>
</repository>

<id> and <name> can be anything you want, as long as id is unique. The most
    important part is the url, where:
[username] is your github username
[repo-name] is the name of your github repository where your maven repository
    is published.

*** once installed in the github maven repository, your jar can be used in your
    project by adding the following dependency to your pom.xml:

<dependency>
    <groupId>[groupId]</groupId>
    <artifactId>[artifactId]</artifactId>
    <version>[version]</version>
</dependency>