#Centralized Configuration Service based on Spring Cloud Config. Server part.

The source of properties could be any mode of storage for e.g. Git Repository, Database, File System, etc.
The default option comes with Git

On running server the Git-backed configuration API provided by our server can be queried using the following paths on `http://localhost:8888`:
```
/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}.yml
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties
```
* `application` - value can be stored at client setting `spring.application.name` but at `spring.cloud.config.name` is preferable
* `profile` - value from `spring.profile.active`. Profiles are loaded in the order of enumeration. 
When there are default property (application.properties) and profiled settings (application-profile.properties) then at the beginning default is loaded and profiled after. 
* `label` - value from client setting `spring.cloud.label`. This value corresponds to git branch name. Very important to know that branch name can't contain slash("/").

According to difference in git versions there is server config property `spring.cloud.config.server.git.default-label`. For example `main` or `master` values. 