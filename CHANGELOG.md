# Redis-Commander CHANGELOG

## Next Version

## Version 0.9.1
#### Bugfixes
* fix bug with docker variables used by REPLACE_CONFIG_ENV containing some special characters
* update express from 4.21.1 to 4.21.2 (fix CVE-2024-52798)
* update cross-spawn from 7.0.3 to 7.0.6 (fix CVE-2024-21538)  
* update base image to Alpine@3.21 and Node.js@22 
* update bcrypt from 5.2.1 to 6.0.0 (fix SNYK-JS-INFLIGHT-6095116 for production image)
* update elliptic from 6.6.0 to 6.6.1 (fix SNYK-JS-ELLIPTIC-8720086)
* update @babel/helpers from 7.26.7 to 7.26.10 (fix CVE-2025-27789)
* update tarfs from 2.1.2 to 2.1.3 (fix CVE-2025-48)
* update pbkdf2 from 3.1.2 to 3.1.3 (fix CVE-2025-6545, CVE-2025-6547)
* update brace-expansion from 1.1.11 to 1.1.12 (fix CVE-2025-5889)

#### Enhancements
* update ioredis from 5.4.1 to 5.5.0
* update chai from 4.5.0 to 5.2.1
* update mocha from 11.1.0 to 11.7.1

## Version 0.9.0
#### Bugfixes
* update jsonwebtoken from 8.5.1 to 9.0.0 (fix CVE-2022-23529, CVE-2022-23541, CVE-2022-23539, CVE-2022-23540)
* update json5 from 2.2.1 to 2.2.3 (fix CVE-2022-46175)
* update cmdparser from 0.0.3 to 0.1.0 (fix CVE-2021-43138), #517
* partial update of semver to 7.5.4 (fix CVE-2022-2588)
* update @babel/traverse from 7.22.5 to 7.23.3 (fix CVE-2023-45133) 
* update browserify-sign from 4.2.1 to 4.2.2 (fix CVE-2023-46234)
* update elliptic from 6.5.4 to 6.6.0 (fix CVE-2024-42459, CVE-2024-42460, CVE-2024-42461, CVE-2024-48948)
* update cookie from 0.6.0 to 0.7.1 (fix CVE-2024-47764)

#### Enhancements
* allow using IPv6 addresses for Redis connection definitions. (except REDIS_HOSTS env var, here no IPv6 allowed, use host names instead) 
* allow setting a custom HTTP header name used for the JWT session authentication token
* add option to overwrite global folding character per connection
* add Sentinel TLS connections and improved configuration and env var handling for TLS secured connections, #514 
* add Redis Cluster support, #160 #216 #527
* allow defining additional commands as safe for read-only mode, defaulting to "info" and "select", #542
* update base image to alpine@3.17 using NodeJS 18.x now, #511
* update helm chart autoscaling apis for newer K8s versions, #520
* update helm chart to allow setting ingressClassName for newer K8s versions, #494
* update UI for better visibility on how to close redis commands modal, #456
* update ioredis from 4.28.5 to 5.4.1
* update dependencies yargs@17.7.2, ejs@3.1.10, jstree@3.3.17, config@3.3.12, body-parser@1.20.3
* update "@cyclonedx/cyclonedx-npm"@1.19.3
* improve password login check and prevent timing attacks on username check

## Version 0.8.1
#### Bugfixes
* fix text not copied when in json view mode
* fix display of big integer and float numbers in json view, #479
* update to alpine:3.16 as base image, #495
* update shell-quote from 1.7.2 to 1.7.3 (fix CVE-2021-42740)
#### Enhancements
* display ReJSON data as formatted json with support for big numbers and floats, #478
* add editing ReJSON data, #452
* update dependencies to fix security vulnerabilities in ansi-regex@5.0.1, filelist@1.0.4, minimatch@3.1.2, shell-quote@1.7.3
* update dependencies express@4.18.2, body-parser@1.20.1, ejs@3.1.8, async@3.2.4, clipboard@2.0.11, yargs@17.6.0, inflection@1.13.4. config@3.3.8
* improve documentation, #498 #500 #506
* add software bill of material in CycloneDX format

## Version 0.8.0
#### Bugfixes
#### Enhancements
* update dependencies to fix security vulnerabilities in minimist, json-viewer, async, config, clipboard
* make url path of signin route configurable (config file and env var), #467
* add redis username and sentinel username support, #476
* update helm chart to allow setting redis username
* fix json display of big numbers not fitting into javascript "number" type, #400

## Version 0.7.3
#### Bugfixes
#### Enhancements
* minimum node version supported 12.x
* update ejs from 2.7.4 to 3.1.6
* update dependencies to fix vulnerabilities in async, tar, yargs, async, ejs, cached-path-relative
* add new import/export function with redis DUMP command and base64 encoded content to work around problems with
* update base image to Alpine 3.15 with NodeJS 16

## Version 0.7.2
#### Bugfixes
#### Enhancements
* update dependencies to fix vulnerabilities in async, tar, yargs, async, ejs, cached-path-relative
* update documentation regarding command line params and environment variables
* update kubernetes examples for seccomp/apparmor profile and not mounting service account token
* update helm chart for service accounts and account token mount
  multi-line redis values or some special data types and binary values

## Version 0.7.2
#### Bugfixes
#### Enhancements
* check for jwt token algorithms used to reject "none" algorithm 
* update dependencies to fix vulnerabilities in elliptic and some other
* add helper script to generated bcrypt password hash and allow setting http auth password hash from file inside docker, #434
* update base image to alpine:3.12
* switch from node-redis-dump to node-redis-dump2 and remove now obsolete docker build patch

## Version 0.7.1
#### Bugfixes
* update handling of big numbers displayed as json formatted values. For big numbers wrong values may be shown, #400 
* increase width of cli input to use full width available, #404 
* fix problem not setting sentinel password from command line, #416
* fix missing quotes for keys with a backslash, #421
* fix possible bug comparing sentinel connections
* block "monitor" at cli to not block redis connections, #424
* fix bug showing additional white spaces in edit hash popup, #426
* fix bug wih config validation for boolean values
* validate urlPrefix config param given for correct use of slashes (start+trailing), #419

#### Enhancements
* Adding maxHashFieldSize config to limit the size of hash fields, #409 (chrisregnier)
* set user in Dockerfile as numeric value to allow Kubernetes to enforce non-root user
* update Kubernetes examples with security settings for Redis Commander
* add config examples for starting Redis Commander with SystemD or PM2, #158
* allow flagging redis connection as optional, if true no permanant auto-reconnect is tried if server is down, reconnection done on request only, #230
* add basic helm chart for k8s installation, based on PR by @aabdennour, #412
* allow partial export of redis data
* add function to rename existing keys, #378
* update dependencies to fix vulnerabilities in multiple packages
* better handle special chars and spaces inside env vars given to docker container

## Version 0.7.0
#### Bugfixes
* fix error on Windows on getting package installation path, #388
* fix wrong connection info data shown on import and export page (sentinel and sockets)

#### Enhancements
* update dependencies to fix vulnerabilities in multiple packages
* change deprecated package "optimist" to "yargs" to fix prototype pollution in dependent minimist package
* add new route /sso to login with signed Json Web Token from external apps with a PSK

#### Breaking Change
* Base image changed from end-of-life Node-8 to pure Alpine 3.11, booth package managers (npm and yarn)
  are available but installed as system package now under different path (`/usr/bin`).
  This change is relevant only when this image is used as base image for other container.
     
## Version 0.6.7
#### Bugfixes
* do not display content of passwords read from env var or file on docker startup, #372
* fix display errors on early display of import/export page
* dependency updates for security fixes (elliptic) and change runtime umask to 027
* fix problem with sentinel connections without explict group name given, #381
* fix problem not showing all nodes after refresh (menu entry), #382

#### Enhancements
* add new docker env vars to load passwords from file (REDIS_PASSWORD_FILE, SENTINEL_PASSWORD_FILE), #364
* add docker image HEALTHCHECK command
* add basic support to display redis string values as hex values, #140
* add basic support to display ReJSON type data, #371
* switch library to display json objects from "json-tree" to "jquery.json-viewer", #375
* add config value and env var to display valid json data as default as formatted json tree object (VIEW_JSON_DEFAULT), #375  
* add config value and env var to disable display of strings as hexadecimal binary data (BINARY_AS_HEX), #376
* add basic validation to redis connection params given via command line and config files, #377
* allow docker image security scanner to work even if apk related files are removed
* add json formatted view to List, Set and SortedSet elements too

## Version 0.6.6
#### Bugfixes
* fix display bug for keys starting with configured foldingchar, #355
* fix bug where cli params do not overwrite other config params, #354
* fix handling of some special chars inside env vars at docker startup script
* disable MULTI command via redis cli to prevent crashes, #358
* fix double html encoding of key data, #362

#### Enhancements
* dependencies updated to fix security problems
* add valid url on startup to access redis commander via browser
* improve console log message for redis connection errors
* add dialog for auto-detection of used redis databases, #121
* change api content-type of methods to "application/json" and move arrays returned down into json object "data" property

## Version 0.6.5
#### Bugfixes
* fix display of keys having multiple consecutive folding chars, #342
* fix connection id handling for node >= 10.x, #270
* fix setting initial ui.locked, cliOpen and height from config file

#### Enhancements
* add redis stream support (display, add, delete), thanks to Adrian Oanca and vflopes
* fix redis sentinel connection handling and make it configurable via config file too
* allow configuration of max allowed request body size via env var or config file, #352
* add json view to hash sets
* improve logging if run behind http reverse proxy like nginx, add config setting and env var, #348
* some ui improvements
* some dependencies updated to fix security problems
* improve documentation

## Version 0.6.4
#### Bugfixes
* fix redis connections via unix sockets, #270
* build redis server command list dynamically to allow usage of all new redis commands via cli (read-write and read-only mode), #210
#### Enhancements
* some ui improvements
* some dependencies updated to fix security problems

## Version 0.6.3
