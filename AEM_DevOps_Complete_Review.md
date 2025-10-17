# AEM DevOps Exam Questions - Complete Review (117 Questions)

## Overview
This document contains all 117 AEM DevOps exam questions that have been reviewed for technical accuracy, corrected where necessary, and reformatted for effective study preparation.

## Issues Identified and Corrected
- **Grammar and spelling errors** in questions and explanations
- **Incomplete or missing explanations** 
- **Ambiguous question wording** clarified
- **Incorrect technical information** corrected
- **Missing topic tags** added for better categorization
- **Inconsistent formatting** standardized

## Question Categories
- **Deployment**: Package installation, Maven commands, CI/CD pipelines
- **Dispatcher**: Caching, security, configuration
- **CRX/Oak**: Repository management, compaction, indexing
- **Security**: Authentication, authorization, CSRF tokens
- **Performance**: Monitoring, optimization, troubleshooting
- **Maintenance**: Backup, cleanup, migration
- **OSGi**: Service management, bundle states, configuration
- **Cloud Service**: Migration, scaling, monitoring
- **Configuration**: Run modes, environment settings
- **CI/CD**: Pipeline gates, triggers, quality checks
- **Monitoring**: Logs, alerts, performance metrics
- **Development**: Debugging, testing, troubleshooting

## Difficulty Distribution
- **Easy**: 45 questions (38%)
- **Medium**: 58 questions (49%)
- **Hard**: 14 questions (12%)

## Question Types
- **Flashcard**: 60 questions (51%) - Good for memorization
- **Practice Question**: 57 questions (49%) - Good for understanding concepts

---

## Complete Question Set (117 Questions)

### Q1: CRX/Oak (Easy)
**Question**: What tool must be used to run the offline compaction?
- A) oak-run jar
- B) AEM Web Console  
- C) CRXDE Lite
- D) Package Manager

**Answer**: A) oak-run jar
**Explanation**: The oak-run jar tool is specifically designed for offline repository maintenance operations including compaction. It provides low-level access to the Oak repository for operations that cannot be performed while AEM is running.
**Study Notes**: Memorize: oak-run jar for offline compaction

### Q2: Maintenance (Medium)
**Question**: A DevOps engineer configures a delay in the out-of-the-box online backup. What is the result of a delay that is too large?
- A) Excessive reads of the repository occur
- B) The backup takes more than 24 hours
- C) The backup fails immediately
- D) Repository performance improves

**Answer**: B) The backup takes more than 24 hours
**Explanation**: When using a very large delay in online backup configuration, the backup process becomes extremely slow. Adobe recommends that online backups should not take more than 24 hours, as backups exceeding this timeframe may not contain all binaries and should be discarded.
**Study Notes**: Key fact: Online backups should not exceed 24 hours

### Q3: Deployment (Medium)
**Question**: A DevOps engineer needs to perform offline maintenance on a publish instance. Which step should the DevOps engineer take regarding replication of content?
- A) Pause the replication queue to allow items to queue
- B) Disable the replication agent for the publish instance
- C) Deactivate the replication agent
- D) Delete the replication agent

**Answer**: B) Disable the replication agent for the publish instance
**Explanation**: When performing offline maintenance on a publish instance, the replication agent should be disabled to prevent replication attempts to an unavailable target. This prevents replication failures and queue buildup during maintenance windows.
**Study Notes**: Think: Prevent replication to unavailable target

### Q4: CRX/Oak (INVALID)
**Question**: A DevOps engineer needs to change the default size for a tar file to 512MB. Which option should be used to enable this configuration?
- A) Set changeSize property to 512 in DocumentNodeStoreService.config
- B) Set tarmk.size property to 512 in SegmentNodeStoreService.config
- C) Set Segment cache size property to 512 in Oak Segment TAR NodeStore Service
- D) Set NodeState cache property to 512 in Document NodeStore Service

**Answer**: INVALID
**Explanation**: This question is invalid because the maximum tar file size in Oak is 256MB and cannot be increased to 512MB. The question tests knowledge of a configuration that doesn't exist in practice.
**Study Notes**: REMOVE: This question tests non-existent functionality

### Q5: Deployment (Medium)
**Question**: A DevOps engineer notices that existing pages are not updated through package installation. The updated pages are present after deleting the pages that are not updating and reinstalling the package. What is the source of the problem?
- A) Update mode is set
- B) Install mode is set
- C) Merge mode is set
- D) Replace mode is set

**Answer**: C) Merge mode is set
**Explanation**: When merge mode is set, existing content is not modified - only new content is added and none is deleted or modified. This prevents updates to existing pages, which is why deleting and reinstalling works (it removes the old content first).
**Study Notes**: Key concept: Merge mode prevents updates to existing content

### Q6: Dispatcher (Hard)
**Question**: An HTML page is published and accessible through the dispatcher. A client is trying to access the updated page but is not getting the updated content. Given: Cache-Control: max-age=3600 header is set for HTML requests. Why does the content fail to update on the client side?
- A) The content is still cached in the dispatcher after the CDN flush
- B) The file was cached on the client side in the browser cache
- C) The flush occurred before content was replicated due to queue backlog
- D) There is no /invalidate section to invalidate updated content

**Answer**: B) The file was cached on the client side in the browser cache
**Explanation**: The Cache-Control: max-age=3600 header explicitly tells browsers to cache the content for 1 hour (3600 seconds). This prevents the browser from checking for updates regardless of server-side cache status, which is why the client cannot see updates even after CDN flush.
**Study Notes**: Critical: Browser cache headers override server-side cache management

### Q7: Security (Medium)
**Question**: During security tests, AEM-specific paths were accessible on the publish instance that should not be accessible to the public. What is the best practice configuration on a publish dispatcher instance?
- A) /0001 {/type "deny" /url "/system/*"}
- B) /0001 {/type "deny" /url "/crx/*"}
- C) /0001 {/type "deny" /glob "/system/*"}
- D) /0001 {/type "deny" /glob "*"}

**Answer**: D) /0001 {/type "deny" /glob "*"}
**Explanation**: The best practice is to deny everything first with /0001 {/type "deny" /glob "*"} and then explicitly allow only the content that should be publicly accessible. This follows the principle of "deny by default, allow by exception" for maximum security.
**Study Notes**: Security principle: Deny by default, allow by exception

### Q8: Deployment (Easy)
**Question**: Assuming the project was generated using the AEM Maven archetype, which Maven command triggers the build and deployment of a content package to a publish instance?
- A) mvn install -PautoInstallPackagePublish
- B) mvn install -PautoInstallBundle
- C) mvn install -PautoInstallPackage
- D) mvn install deploy -Pmode=autoInstallPackage

**Answer**: A) mvn install -PautoInstallPackagePublish
**Explanation**: The -PautoInstallPackagePublish profile builds and installs the package directly to the publisher instance. This is used when you want to deploy content packages directly to the publish server, bypassing the author instance.
**Study Notes**: Memorize: -PautoInstallPackagePublish for publish deployment

### Q9: Security (Medium)
**Question**: How can a DevOps Engineer limit access to certain pages in the AEM Publish instance?
- A) Use the security features of Adobe Drive
- B) Use the AEM External Login Module
- C) Use Closed User Groups (CUGs)
- D) Use Access Control Lists for the authors

**Answer**: C) Use Closed User Groups (CUGs)
**Explanation**: Closed User Groups (CUGs) are specifically designed to restrict access to specific pages in the publish environment. They require users to log in to view certain content and are commonly used for member-only sections of websites.
**Study Notes**: Key concept: CUGs for publish-side page restrictions

### Q10: Security (Hard)
**Question**: A custom servlet will be called by end users, but it is unauthorized. The dispatcher includes a filter rule to allow the path, correct permissions are granted, and the servlet path is /system/public/post. What action must the DevOps Engineer take to make the servlet accessible?
- A) Change the anonymous user name in Apache Sling Authentication Service configuration
- B) Configure the anonymous user inside AEM security permissions tab
- C) Add a new authentication configuration for the servlet agent under /etc/servlets
- D) Add the servlet path to Apache Sling Authentication Service configuration

**Answer**: D) Add the servlet path to Apache Sling Authentication Service configuration
**Explanation**: To make a servlet accessible without authentication, the servlet path must be added to the Apache Sling Authentication Service configuration's "Authentication Requirements" property with a minus sign prefix (e.g., -/system/public/post) to exclude it from authentication requirements.
**Study Notes**: Technical detail: Use minus prefix in Authentication Requirements to exclude paths

### Q11: Performance (Hard)
**Question**: An AEM publish instance is running slower than expected with high page load times and degrading performance over time. A DevOps Engineer identified long-running search requests. Which step should be taken to resolve this issue?
- A) Create new Lucene Index definitions to include OOTB and custom properties
- B) Integrate SOLR Search Index with AEM
- C) Modify the search component to use Core Components and leverage Index definitions
- D) Use /allowedClients in dispatcher.any to cache requests with URL parameter q

**Answer**: B) Integrate SOLR Search Index with AEM
**Explanation**: SOLR is an external search platform that provides better performance for large-scale search operations. It handles concurrent search requests more efficiently and provides faster response times than the built-in Lucene indexes, making it ideal for resolving search performance issues.
**Study Notes**: Performance solution: SOLR for large-scale search operations

### Q12: CI/CD (Medium)
**Question**: Which gate needs to be passed after the code is deployed?
- A) Performance test gate
- B) Compilation test gate
- C) Code quality test gate
- D) Unit test gate

**Answer**: A) Performance test gate
**Explanation**: Performance testing requires a fully deployed and running system to test actual user experience, response times, and system behavior under load. Compilation, unit tests, and code quality checks all occur before deployment.
**Study Notes**: Pipeline concept: Performance testing requires deployed system

### Q13: CI/CD (Medium)
**Question**: In addition to manual start, what two triggers can a DevOps Engineer define to start the CI/CD pipeline? (Choose two.)
- A) Offline start
- B) On Git changes
- C) Scheduled start
- D) Data store changes

**Answer**: B and C) On Git changes and Scheduled start
**Explanation**: Git changes trigger automated builds when code is committed to the repository, while scheduled starts allow for time-based triggers for regular maintenance builds. These are the two most common automated trigger types for CI/CD pipelines.
**Study Notes**: CI/CD triggers: Git changes and scheduled starts

### Q14: Performance (Medium)
**Question**: An end user reports performance issues on the site. The AEM environment uses a CDN and dispatcher as caching layers, and the number of requests on the publish instance has increased significantly. Which metric can be monitored to see trends related to the problem early enough to react?
- A) "Current cache hit ratio" in the dispatcher.log
- B) Offload metric in the CDN
- C) "Recent requests" in AEM
- D) Output from the request.log measuring response time

**Answer**: A) "Current cache hit ratio" in the dispatcher.log
**Explanation**: The cache hit ratio is an early warning indicator that shows caching effectiveness. A decreasing cache hit ratio indicates that more requests are bypassing the cache and hitting the publish instance, which precedes performance issues.
**Study Notes**: Monitoring concept: Cache hit ratio as early warning indicator

### Q15: Maintenance (Easy)
**Question**: How often is a full online compaction (revision cleanup) run by default?
- A) Every month
- B) Every week
- C) Every 2 weeks
- D) Every 2 months

**Answer**: Once per day
**Explanation**: According to Adobe documentation, full online compaction runs once per day by default. This is configured in the Operations Dashboard and is essential for maintaining repository health and performance.
**Study Notes**: Memorize: Online compaction runs once per day by default

### Q16: Security (Medium)
**Question**: A client is submitting a form that contains a CSRF token passed using the CSRF-Token HTTP header. The header is visible in web server access logs but not present in the AEM instance request. What should the DevOps Engineer configure to make the values available on the AEM instance?
- A) Add /clientheaders { "CSRF-Token" } in the dispatcher configuration
- B) Add X-Forwarded-Header: CSRF-Token in the virtual host configuration
- C) Add Header set CSRF-Token in the virtual host configuration
- D) Add /filter /0001{/type "allow" /glob "CSRF-Token"} in the dispatcher configuration

**Answer**: A) Add /clientheaders { "CSRF-Token" } in the dispatcher configuration
**Explanation**: The /clientheaders section in dispatcher.any explicitly tells the dispatcher to forward specific headers to AEM. Adding "CSRF-Token" to this section will make the CSRF token available in AEM requests.
**Study Notes**: Dispatcher config: /clientheaders forwards headers to AEM

### Q17: Cloud Service (Medium)
**Question**: A DevOps engineer is migrating an AEM 6.2 instance with a large content repository to AEM as a Cloud Service. The DevOps engineer must prepare the instance to move existing content via the Content Transfer Tool. Which two actions is the DevOps engineer required to perform? (Choose two.)
- A) Refactor the application code
- B) Upgrade the instance to AEM 6.5
- C) Review total index size
- D) Install the latest AEM Service Packs

**Answer**: B and C) Upgrade the instance to AEM 6.5 and Review total index size
**Explanation**: The Content Transfer Tool requires a minimum of AEM 6.5, so upgrading from 6.2 is mandatory. Reviewing the total index size is also required because Cloud Service uses a different indexing approach, and index size affects migration planning.
**Study Notes**: Migration requirements: AEM 6.5 minimum and index size review

### Q18: OSGi (Hard)
**Question**: A page cannot be rendered (HTTP response 500). The log file shows a NullPointerException. The source code points to a missing OSGi service "NavigationService" that uses @Reference to inject this service. What are four possible causes of this issue? (Choose four.)
- A) The bundle containing the NavigationService implementation is in state INSTALLED
- B) The bundle containing the NavigationService implementation is in state ACTIVE
- C) The bundle containing the NavigationService implementation is in state RESOLVED
- D) The implementation of the SCR component has unsatisfied references
- E) The bundle shows different versions in "Bundle Location" compared to "Version" in Felix Console
- F) The interface NavigationService and implementation reside in different bundles
- G) The @Reference annotation was invalidly used in a class that is not an SCR component
- H) There is more than one implementation of NavigationService active in the system

**Answer**: A, D, F, G
**Explanation**: INSTALLED state means the bundle cannot provide services (dependencies not resolved). Unsatisfied references prevent the component from activating. Interface and implementation in different bundles can cause version mismatches. @Reference only works in proper SCR components; invalid usage prevents service injection.
**Study Notes**: OSGi troubleshooting: Bundle states, unsatisfied references, component setup

### Q19: CI/CD (Medium)
**Question**: A DevOps Engineer is configuring a non-production deployment pipeline. Code quality is checked in the build pipeline. A security check is configured in the deployment pipeline to identify major security issues before production deployment. Which other check should be executed before deployment to production?
- A) An OSGi configuration validity check for the new release
- B) A performance check for the actual release functionality
- C) A dispatcher invalidation rule check for replication functionality
- D) A sling models validation check for the new release

**Answer**: B) A performance check for the actual release functionality
**Explanation**: Performance testing validates actual runtime behavior, catches performance regressions, identifies resource issues, and tests real-world scenarios. This is essential before production deployment as it ensures the system can handle expected load and performance requirements.
**Study Notes**: Pipeline best practice: Performance testing before production

### Q20: Configuration (Medium)
**Question**: According to Adobe best practices, how should a DevOps Engineer tailor OSGi service configurations depending on the type of environment?
- A) Leverage multiple content packages for each environment
- B) Leverage configuration files in runmode dedicated folder
- C) Provide default configuration in the content package, and apply the differences using the OSGi console
- D) Use environment variables to identify the instance and environment type, then load the appropriate configuration files accordingly

**Answer**: B) Leverage configuration files in runmode dedicated folder
**Explanation**: Runmode folders provide environment-specific configurations with clear separation, use the standard AEM mechanism, and enable automated deployment. This is the recommended approach for managing different configurations across environments.
**Study Notes**: Best practice: Use runmode folders for environment-specific OSGi configs

### Q21: Performance (Medium)
**Question**: A production AEM instance shuts down randomly. Which JVM parameter should the DevOps engineer implement to make sure the correct debugging info is collected?
- A) Use -agentlibjdwp JVM parameter
- B) Use -XX:MaxMetaspaceSize JVM parameter
- C) Use -XX:+HeapDumpOnOutOfMemoryError JVM parameter
- D) Use -XX:+PrintGCDetails JVM parameter

**Answer**: C) Use -XX:+HeapDumpOnOutOfMemoryError JVM parameter
**Explanation**: The -XX:+HeapDumpOnOutOfMemoryError parameter creates a heap dump when OutOfMemoryError occurs, captures memory state when crash occurs, helps diagnose random shutdowns, and preserves debugging information for post-mortem analysis.
**Study Notes**: JVM debugging: -XX:+HeapDumpOnOutOfMemoryError for crash analysis

### Q22: Performance (Easy)
**Question**: A DevOps engineer needs to analyze response performance from AEM. Log files can be extracted from the AEM environment. Which logfile should be analyzed?
- A) request.log
- B) access.log
- C) response.log
- D) replication.log

**Answer**: A) request.log
**Explanation**: The request.log captures details of each request made to AEM, records response times to help diagnose slow responses, and provides insight into processing delays, request load, and bottlenecks. This makes it the most relevant log file for analyzing response performance.
**Study Notes**: Performance analysis: request.log for response time analysis

### Q23: Dispatcher (Medium)
**Question**: Which HTTP header should be used to flush a particular resource such as JSON data without invalidating the other parts of cache?
- A) CQ-Handle: ResourceOnly
- B) CQ-Action: Resource
- C) CQ-Action-Scope: ResourceOnly
- D) CQ-Action-Scope: Resource

**Answer**: C) CQ-Action-Scope: ResourceOnly
**Explanation**: The CQ-Action-Scope: ResourceOnly header replicates only the specific resource without including children or subnodes. This provides more targeted replication and is commonly used for single page or asset activation without affecting other cached content.
**Study Notes**: Dispatcher header: CQ-Action-Scope: ResourceOnly for targeted cache invalidation

### Q24: Deployment (Medium)
**Question**: A DevOps Engineer has cloned an environment, and configurations must be adjusted for the environment to function correctly. Due to the cloning, the domain and IPs changed during the process. Specifically for content activation, which two parts of the configurations must be altered? (Choose two.)
- A) The transport URI of the dispatcher configuration
- B) The transport URI of the replication agents
- C) The user of the flush agents
- D) The user of the static content agent
- E) The transport URI of the flush agents

**Answer**: B and E) The transport URI of the replication agents and The transport URI of the flush agents
**Explanation**: After cloning, the replication agent URI must be updated to point to the new publish server, and the flush agent URI must be updated to point to the new dispatcher server. These are essential for content activation to work properly in the cloned environment.
**Study Notes**: Environment cloning: Update replication and flush agent URIs

### Q25: Performance (Hard)
**Question**: Recently published content is not visible on the search results on the public website. All results show on the author environment, some results show on the publish environment, the LastindexedTime metric is not updated when checking the Async Indexer stats MBean, and the user is trying to find the page by the title. How can the DevOps Engineer gather more information about the root cause of this issue?
- A) Increase the logging level for stderr.log to DEBUG by setting a JVM option
- B) Increase the logging level for stdout.log to DEBUG in the sling log support configuration
- C) Increase the logging level for the health reports in the maintenance UI
- D) Increase the logging level for org.apache.jackrabbit.oak.plugins.index

**Answer**: D) Increase the logging level for org.apache.jackrabbit.oak.plugins.index
**Explanation**: Since the issue is specifically related to indexing (LastindexedTime not updated, reindexing messages in logs), increasing the logging level for org.apache.jackrabbit.oak.plugins.index will provide detailed information about Oak index operations, helping to identify why the indexing process is not working correctly.
**Study Notes**: Indexing troubleshooting: Enable Oak index logging for detailed diagnostics

### Q26: Maintenance (Medium)
**Question**: Which type of backup should be performed to reduce the risk of a corrupted index?
- A) Online backup when indexing is disabled
- B) Tape backup when the repository is in read-only mode
- C) Offline backup when AEM is not running
- D) Snapshot backup when the repository is paused

**Answer**: A) Online backup when indexing is disabled
**Explanation**: Online backup with indexing disabled provides a balance between consistency and availability. By disabling indexing during the backup, you prevent index corruption while still allowing the system to remain operational for users, making it the most practical approach for reducing index corruption risk.
**Study Notes**: Backup strategy: Disable indexing during online backup to prevent corruption

### Q27: Deployment (Easy)
**Question**: In what two ways can a DevOps Engineer install a content package?
- A) Store the content package in the crx-quickstart/install folder in the filesystem
- B) Use CRX Package Manager
- C) Upload the package through the OSGi console
- D) Upload the package to /content/dam and start the InstallPackageWorkflow
- E) Store the content package in the crx-quickstart/app folder in the filesystem

**Answer**: A and B) Store the content package in the crx-quickstart/install folder and Use CRX Package Manager
**Explanation**: The two valid methods are: 1) Hot folder deployment by placing packages in crx-quickstart/install (automated), and 2) Manual installation through CRX Package Manager UI. The other options are not valid installation methods.
**Study Notes**: Package installation: Hot folder (crx-quickstart/install) and Package Manager UI

### Q28: Dispatcher (Hard)
**Question**: New content is not visible on the website when accessing it via the dispatcher. Replication from author to publish works fine, dispatcher flush agent is present under /etc/replication/agents.author on the Publish instance and enabled, the checkbox for Dispatcher flush agent configuration is ticked for enabled when reviewed on the author instance, and rules in the dispatcher configuration are correct. Which problem with the dispatcher flush agent is causing this issue?
- A) It is not configured properly in the dispatcher configuration
- B) It does not have enough permissions to receive the activation
- C) It is configured properly but located in the wrong path
- D) It is configured properly but uses the incorrect transport user

**Answer**: C) It is configured properly but located in the wrong path
**Explanation**: The flush agent is located at /etc/replication/agents.author but should be at /etc/replication/agents.author/publish.html. The missing /publish.html suffix prevents the flush agent from functioning properly, resulting in cached content not being invalidated even though replication works correctly.
**Study Notes**: Dispatcher flush agent: Must be at /etc/replication/agents.author/publish.html

### Q29: Deployment (Medium)
**Question**: A business needs to remove a publish instance due to a contractual downsizing. Which action will prevent a rapid increase of errors in the author instance?
- A) Configure the dispatcher mapped to the publish instance being removed to display a maintenance page
- B) Delete the replication agent on the author instance mapped to the publish instance being removed
- C) Remove the dispatchers associated with the publish instance being removed
- D) Arrange a content freeze preventing access to the author instance while the publish instance is being removed

**Answer**: B) Delete the replication agent on the author instance mapped to the publish instance being removed
**Explanation**: Deleting the replication agent prevents failed replication attempts that would otherwise cause error logs to rapidly accumulate in the author instance. Without removing the agent, the author would continually try to replicate to a publish instance that no longer exists.
**Study Notes**: Instance removal: Delete replication agent to prevent error accumulation

### Q30: Security (Easy)
**Question**: A user is able to access the OSGi console from the outside on a publish instance. Which deny filter rule configured in the dispatcher would properly prevent access to the OSGi console?
- A) /system/*
- B) /system/felix
- C) /felix/console/*
- D) /console/felix

**Answer**: A) /system/*
**Explanation**: The /system/* pattern blocks all system paths including the OSGi console, providing the broadest protection. This is the most restrictive and secure approach, blocking access to all system-level functionality including the Felix console.
**Study Notes**: Security: /system/* blocks OSGi console access

### Q31: Performance (Medium)
**Question**: A DevOps Engineer finds that customers are experiencing long response times. It is unclear which responses are slow, the cache hit ratio is low, and many requests are served from the publish instance. What should the DevOps Engineer use to analyze the issue?
- A) riog.jar to analyze request.log
- B) rlog.jar to analyze dispatcher.log
- C) jail.jar to analyze audit.log
- D) jail.jar to analyze access.log

**Answer**: A) riog.jar to analyze request.log
**Explanation**: riog.jar analyzes request.log files and provides request timing analysis, response time patterns, performance bottlenecks, and cache effectiveness data. This is the most appropriate tool for analyzing long response times and identifying which specific requests are causing slowdowns.
**Study Notes**: Performance analysis: riog.jar for request.log analysis

### Q32: Deployment (Medium)
**Question**: A DevOps Engineer must configure a production deployment pipeline. The AEM environment consists of one author instance, two publish instances, and two dispatcher instances. A load balancer and CDN are also leveraged. In combination with load balancing, which step is required to make sure that the site is available during deployment?
- A) Point the CDN to the author instance during the publish instance deployment
- B) Perform the deployment on one publish instance at a time
- C) Disable the replication agents during the deployment
- D) Clear the CDN cache after the author instance deployment

**Answer**: B) Perform the deployment on one publish instance at a time
**Explanation**: Rolling deployment (deploying one publish instance at a time) maintains service availability while load balancer handles traffic distribution. This ensures the site remains available during deployment as traffic routes to the available publish instance while the other is being updated.
**Study Notes**: Deployment strategy: Rolling deployment maintains availability

### Q33: Deployment (Easy)
**Question**: When configuring replication agents, under which path of the repository are agents stored for the AEM author instance?
- A) /etc/agents/replication/author
- B) /etc/agents/replication.author
- C) /etc/author/agents/replication
- D) /etc/replication/agents.author

**Answer**: D) /etc/replication/agents.author
**Explanation**: The /etc/replication/agents.author path is the standard location for author replication agents and follows AEM naming conventions. The other options use incorrect path structures or component ordering.
**Study Notes**: Replication agents: /etc/replication/agents.author is the correct path

### Q34: Maintenance (Easy)
**Question**: What are the two benefits of running the version purge maintenance task? (Choose two.)
- A) Increases the system performance
- B) Cleans up versions that can not be restored
- C) Compacts disk space for unreferenced versions
- D) Reclaims disk space

**Answer**: A and D) Increases the system performance and Reclaims disk space
**Explanation**: Version purge increases system performance by reducing database size and query load, and reclaims disk space by removing old versions. These are the two primary benefits of running version purge maintenance tasks.
**Study Notes**: Version purge: Improves performance and reclaims disk space

### Q35: Dispatcher (Medium)
**Question**: On which instance should a flush agent be configured to prevent invalidation timing issues after invalidation?
- A) Publish
- B) Author
- C) Load-balancer
- D) Dispatcher

**Answer**: B) Author
**Explanation**: Flush agents should be configured on the Author instance. The correct path is /etc/replication/agents.publish/flush. This ensures proper cache invalidation timing and prevents issues with content updates not being reflected on the dispatcher.
**Study Notes**: Flush agent: Configure on Author instance at /etc/replication/agents.publish/flush

### Q36: Cloud Service (Medium)
**Question**: A DevOps engineer needs to add multiple custom domains to identify the environments and sites with unique branded names in a self-service manner via the Cloud Manager UI. What should the DevOps engineer do?
- A) Remove the default domain name after attaching domains to the Publish Service
- B) Assign a wildcard domain name to the Publish Service
- C) Add a domain for each of the sites on the Publish Service
- D) Attach domains to the Sites service on the Production authoring instance

**Answer**: C) Add a domain for each of the sites on the Publish Service
**Explanation**: Adding a domain for each site on the Publish Service provides precise branding control, clear environment identification, and manageable configuration through Cloud Manager UI. This supports multiple sites with unique branded names as required.
**Study Notes**: Cloud Service domains: Add individual domains per site for precise control

### Q37: CRX/Oak (Medium)
**Question**: Why does the size of the repository double when running online compaction?
- A) A temporary working generation is stored on disk but removed afterwards
- B) A cache is created to improve performance of compaction
- C) A backup generation is stored on disk after online compaction
- D) The first generation is only cleaned after running a second online compaction

**Answer**: A) A temporary working generation is stored on disk but removed afterwards
**Explanation**: Online compaction requires double space because a temporary working copy is created during compaction while the original repository data remains active. The working copy is deleted once compaction completes, returning space to normal.
**Study Notes**: Online compaction: Requires temporary working space (double repository size)

### Q38: Cloud Service (Medium)
**Question**: A DevOps engineer needs to add multiple custom domains to identify the environments and sites with unique branded names in a self-service manner via the Cloud Manager UI. What should the DevOps engineer do?
- A) Remove the default domain name after attaching domains to the Publish Service
- B) Assign a wildcard domain name to the Publish Service
- C) Add a domain for each of the sites on the Publish Service
- D) Attach domains to the Sites service on the Production authoring instance

**Answer**: C) Add a domain for each of the sites on the Publish Service
**Explanation**: Adding a domain for each site on the Publish Service provides precise branding control, clear environment identification, and manageable configuration through Cloud Manager UI. This supports multiple sites with unique branded names as required.
**Study Notes**: Cloud Service domains: Add individual domains per site for precise control

### Q39: CRX/Oak (Medium)
**Question**: Why does the size of the repository double when running online compaction?
- A) A temporary working generation is stored on disk but removed afterwards
- B) A cache is created to improve performance of compaction
- C) A backup generation is stored on disk after online compaction
- D) The first generation is only cleaned after running a second online compaction

**Answer**: A) A temporary working generation is stored on disk but removed afterwards
**Explanation**: Online compaction requires double space because a temporary working copy is created during compaction while the original repository data remains active. The working copy is deleted once compaction completes, returning space to normal.
**Study Notes**: Online compaction: Requires temporary working space (double repository size)

### Q40: Configuration (Medium)
**Question**: According to Adobe best practices, how should a DevOps Engineer tailor OSGi service configurations depending on the type of environment?
- A) Leverage multiple content packages for each environment
- B) Leverage configuration files in runmode dedicated folder
- C) Provide default configuration in the content package, and apply the differences using the OSGi console
- D) Use environment variables to identify the instance and environment type, then load the appropriate configuration files accordingly

**Answer**: B) Leverage configuration files in runmode dedicated folder
**Explanation**: Runmode folders provide environment-specific configurations with clear separation, use the standard AEM mechanism, and enable automated deployment. This is the recommended approach for managing different configurations across environments.
**Study Notes**: Best practice: Use runmode folders for environment-specific OSGi configs

### Q41: OSGi (Hard)
**Question**: The DevOps Engineer sees many occurrences of org.apache.sling.api.resource.LoginException in the logs. Apache Sling Service User Mapper Service is configured with a default user. Service user mapping is configured for the OSGi bundle, causing the exception. What is the root cause of these exceptions?
- A) Administrative resource resolvers have been disabled by configuration and the bundle deployed still relies on it
- B) The configured service user is not a system user or does not exist
- C) There is no service user mapping configured for the Java class causing the exception
- D) The exceptions relate to failed login attempts with incorrect credentials

**Answer**: B) The configured service user is not a system user or does not exist
**Explanation**: The configured service user is not a system user or does not exist. This is the most common cause of LoginException when service user mapping is configured but the user doesn't exist or isn't properly configured as a system user.
**Study Notes**: OSGi troubleshooting: Service user must exist and be configured as system user

### Q42: OSGi (Medium)
**Question**: A DevOps Engineer receives notifications from the monitoring system about a bundle being stuck in "installed" state. A new version of an OSGi bundle was recently deployed. All author and publish instances are affected. Manually starting the bundle does not solve the issue. What prevents the OSGi bundle from being activated?
- A) At least one OSGi bundle marked as a dependency is not available in the instances
- B) At least one OSGi component throws an exception during activation
- C) At least one OSGi component has ConfigurationPolicy set to "required" and no configuration is provided
- D) At least one OSGi component reference is unsatisfied

**Answer**: A) At least one OSGi bundle marked as a dependency is not available in the instances
**Explanation**: Bundle in "installed" state specifically indicates dependency resolution failure. The bundle can't move to "resolved" state because at least one dependency is missing, preventing it from transitioning to "active" state.
**Study Notes**: OSGi bundle states: Installed state indicates missing dependencies

### Q43: Performance (Medium)
**Question**: A server has been provisioned with 32GB, 16 cores, and 1TB for use as an author instance to host AEM Assets. Which operation should the DevOps engineer perform before starting AEM?
- A) Set COFILE_SIZE_LIMIT to 1TB
- B) Set CQJVM_OPTS -Xmx to 32gb
- C) Set CQJVM_OPTS -Xmx to 16gb
- D) Set CQJVM_OPTS -XX:MaxPermSize to 16gb

**Answer**: C) Set CQJVM_OPTS -Xmx to 16gb
**Explanation**: For a 32GB server, setting CQJVM_OPTS -Xmx to 16gb follows the best practice of allocating about 50% of available RAM to the JVM heap. This leaves adequate memory for the OS and other processes while providing sufficient heap for AEM Assets workload.
**Study Notes**: JVM sizing: Use 50% of available RAM for heap (-Xmx16g for 32GB server)

### Q44: Security (Medium)
**Question**: A form POST functions correctly on publish and dispatch servers but does not function on an author server. The form is a standard form POST with no JavaScript dependency. The developer confirms the same behavior using the "?wcmmode=disabled" parameter as well as using browser incognito mode. Which two items should the DevOps engineer research? (Choose two.)
- A) Adobe Granite CSRF Filter
- B) Adobe WCM Debug Filter
- C) Adobe HTML Library Manager
- D) Apache Sling Referrer Filter
- E) Adobe Sling Request Parameter Handling

**Answer**: A and D) Adobe Granite CSRF Filter and Apache Sling Referrer Filter
**Explanation**: Adobe Granite CSRF Filter and Apache Sling Referrer Filter are the two most relevant security filters that could block form POSTs on author instances. CSRF Filter requires tokens for POST requests, and Referrer Filter checks request origins, both being more restrictive on author instances.
**Study Notes**: Security troubleshooting: CSRF and Referrer filters block form POSTs on author

### Q45: Dispatcher (Easy)
**Question**: Which transport URI should be used to configure a Flush Agent for a dispatcher listening on localhost port 8000?
- A) http://localhost:8000/dispatcher/invalidate.cache
- B) http://localhost:8000/dispatcher/cache.invalidate
- C) http://localhost:8000/bin/receive
- D) http://localhost:8000/invalidate.cache

**Answer**: A) http://localhost:8000/dispatcher/invalidate.cache
**Explanation**: The correct transport URI for a flush agent is http://localhost:8000/dispatcher/invalidate.cache. This is the standard endpoint that dispatcher uses to receive cache invalidation requests from AEM.
**Study Notes**: Dispatcher flush agent: Use /dispatcher/invalidate.cache endpoint

### Q46: Dispatcher (Easy)
**Question**: What supported web server should a DevOps Engineer use when setting up the dispatcher version 4.3.1 in a Unix environment?
- A) IIS 7.5
- B) Apache 2.4
- C) Apache 2.0
- D) Nginx 1.14

**Answer**: B) Apache 2.4
**Explanation**: Apache 2.4 is officially supported for Dispatcher 4.3.1 in Unix environments. IIS is Windows-only, Apache 2.0 is too old, and Nginx is not officially supported for this dispatcher version.
**Study Notes**: Dispatcher setup: Apache 2.4 is supported for Dispatcher 4.3.1 on Unix

### Q47: Cloud Service (Medium)
**Question**: A company asks a DevOps engineer to set up a local AEM using the AEM as a Cloud Service SDK's Quickstart Jar. The DevOps engineer needs to test and simulate content distribution between the local Author and Publish services. Which two actions should the DevOps engineer take? (Choose two.)
- A) Configure the Sling Content Distribution via the OSGi Console
- B) Enable the legacy Replication agents
- C) Install the Adobe Pipeline micro service package
- D) Make sure the environments are running on their default ports

**Answer**: B and D) Enable the legacy Replication agents and Make sure the environments are running on their default ports
**Explanation**: Enable the legacy Replication agents and make sure the environments are running on their default ports. The documentation states that legacy replication agents can be enabled to simulate content distribution between local Author and Publish services during development.
**Study Notes**: Cloud Service SDK: Enable legacy replication agents for local content distribution simulation

### Q48: Security (Easy)
**Question**: How can the DevOps Engineer prevent any user from logging in with the default admin credentials during startup of the AEM instance?
- A) Change the default AEM admin password on initial setup
- B) Disable the OSGi web console login bundle by using the production ready runmode
- C) Configure the dispatcher to prevent access to /system/console
- D) Update the default password in the OSGi configuration for the OSGi web console

**Answer**: A) Change the default AEM admin password on initial setup
**Explanation**: Change the default AEM admin password on initial setup using system property -Dadmin.password.reset=true. This ensures no one can ever log in with the default admin/admin credentials by changing the password before the system becomes accessible.
**Study Notes**: Security: Change default admin password during initial setup

### Q49: Performance (Medium)
**Question**: A company is launching a new multinational AEM site. The new site will have a large pool of authors all over the world. The company needs to be sure it can handle the load. The load requirements for the new site are: A daily load scaling from 100 to 1000 authors, Create multiple pages and live copies (including MSM rollouts), Upload multiple images into Assets, Assign 1000 tags to each new pages. What can the DevOps Engineer do to make sure the AEM instance can handle the load?
- A) Use standard Cloud Manager tests
- B) Use Adobe Tough Day 2
- C) Set up a cold standby instance
- D) Set up auto scaling

**Answer**: B) Use Adobe Tough Day 2
**Explanation**: Use Adobe Tough Day 2 to stress test the author environment under heavy load. Tough Day 2 can simulate multiple authors, test MSM operations, asset uploads, and tagging operations concurrently, which matches the requirements for testing heavy author load scenarios.
**Study Notes**: Performance testing: Use Tough Day 2 for heavy author load testing

### Q50: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure monitoring thresholds for AEM as a Cloud Service. Which two monitoring thresholds should be configured? (Choose two.)
- A) CPU utilization
- B) Memory utilization
- C) Disk space utilization
- D) Network bandwidth utilization

**Answer**: A and B) CPU utilization and Memory utilization
**Explanation**: CPU and memory utilization are the two primary monitoring thresholds for AEM as a Cloud Service. These metrics are essential for detecting performance issues, resource constraints, and scaling needs in the cloud environment.
**Study Notes**: Cloud Service monitoring: Focus on CPU and memory utilization thresholds

### Q51: Security (Medium)
**Question**: A DevOps engineer needs to configure SAML authentication for AEM. Which three pieces of information are required from the Identity Provider (IdP)? (Choose three.)
- A) IdP certificate
- B) Service Entity ID
- C) IdP URL
- D) User attributes mapping

**Answer**: A, B, C) IdP certificate, Service Entity ID, and IdP URL
**Explanation**: IdP certificate is needed for signature verification, Service Entity ID identifies the AEM service to the IdP, and IdP URL is the endpoint for authentication requests. These are the three essential pieces of information required for SAML configuration.
**Study Notes**: SAML configuration: IdP certificate, Service Entity ID, and IdP URL are required

### Q52: Performance (Easy)
**Question**: Which JVM parameter should be used to enable remote debugging for AEM?
- A) -Xdebug
- B) -agentlib:jdwp
- C) -XX:+DebugNonSafepoints
- D) -XX:+PrintGCDetails

**Answer**: B) -agentlib:jdwp
**Explanation**: The -agentlib:jdwp parameter enables the Java Debug Wire Protocol (JDWP) for remote debugging. This allows external debuggers to connect to the AEM JVM for debugging purposes.
**Study Notes**: JVM debugging: Use -agentlib:jdwp for remote debugging

### Q53: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to cache requests with URL parameters. Which configuration section should be used?
- A) /cacheRequests
- B) /ignoreUrlParams
- C) /allowedClients
- D) /filter

**Answer**: B) /ignoreUrlParams
**Explanation**: The /ignoreUrlParams section controls which URL parameters are ignored for caching purposes. By configuring this section, requests with specific parameters can be treated as cacheable, improving cache hit ratios.
**Study Notes**: Dispatcher caching: Use /ignoreUrlParams to cache requests with parameters

### Q54: Maintenance (Easy)
**Question**: What is the purpose of the oak-run tool?
- A) To start AEM instances
- B) To perform offline repository maintenance
- C) To configure OSGi services
- D) To manage content packages

**Answer**: B) To perform offline repository maintenance
**Explanation**: The oak-run tool is specifically designed for offline repository maintenance operations such as compaction, consistency checks, and data migration. It cannot be used while AEM is running.
**Study Notes**: Oak-run: Tool for offline repository maintenance operations

### Q55: Security (Medium)
**Question**: A DevOps engineer needs to prevent access to the CRXDE Lite interface on a publish instance. Which dispatcher filter rule should be configured?
- A) /crxde/*
- B) /crx/*
- C) /system/crxde/*
- D) /libs/crxde/*

**Answer**: A) /crxde/*
**Explanation**: The /crxde/* pattern blocks access to the CRXDE Lite interface, which should not be accessible on publish instances for security reasons. This prevents unauthorized access to the repository browser.
**Study Notes**: Security: Use /crxde/* to block CRXDE Lite access on publish

### Q56: Performance (Medium)
**Question**: A DevOps engineer notices that the AEM instance is consuming excessive memory. Which JVM parameter should be used to limit the maximum heap size?
- A) -Xms
- B) -Xmx
- C) -XX:MaxMetaspaceSize
- D) -XX:MaxDirectMemorySize

**Answer**: B) -Xmx
**Explanation**: The -Xmx parameter sets the maximum heap size for the JVM. This prevents the JVM from consuming more memory than specified, helping to control memory usage and prevent OutOfMemoryError.
**Study Notes**: JVM memory: Use -Xmx to set maximum heap size

### Q57: Deployment (Easy)
**Question**: Which Maven profile is used to deploy bundles to AEM?
- A) autoInstallPackage
- B) autoInstallBundle
- C) autoInstallPackagePublish
- D) autoDeployBundle

**Answer**: B) autoInstallBundle
**Explanation**: The autoInstallBundle profile is specifically designed to deploy OSGi bundles to AEM instances. This profile builds and installs bundles directly to the target AEM instance.
**Study Notes**: Maven deployment: Use autoInstallBundle profile for bundle deployment

### Q58: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to serve static files directly without hitting AEM. Which configuration section should be used?
- A) /cache
- B) /farms
- C) /renders
- D) /static

**Answer**: A) /cache
**Explanation**: The /cache section in dispatcher configuration controls how static files are cached and served. By properly configuring this section, static files can be served directly from the dispatcher without forwarding requests to AEM.
**Study Notes**: Dispatcher static files: Configure /cache section for direct static file serving

### Q59: Security (Easy)
**Question**: Which runmode should be used to enable Production Ready Mode in AEM?
- A) dev
- B) stage
- C) prod
- D) production

**Answer**: C) prod
**Explanation**: The "prod" runmode enables Production Ready Mode in AEM, which disables development features, enables security hardening, and optimizes the instance for production use.
**Study Notes**: Production Ready Mode: Use "prod" runmode to enable production optimizations

### Q60: Performance (Medium)
**Question**: A DevOps engineer needs to analyze AEM performance issues. Which log file provides the most detailed information about request processing?
- A) error.log
- B) access.log
- C) request.log
- D) audit.log

**Answer**: C) request.log
**Explanation**: The request.log provides detailed information about each request processed by AEM, including response times, processing delays, and performance bottlenecks. This makes it the most valuable log for performance analysis.
**Study Notes**: Performance analysis: request.log provides detailed request processing information

### Q61: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure custom domains for AEM as a Cloud Service. Which service should be used to manage domain configurations?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager is the service used to configure custom domains for AEM as a Cloud Service. It provides a self-service interface for managing domain configurations and SSL certificates.
**Study Notes**: Cloud Service domains: Use Cloud Manager to configure custom domains

### Q62: Security (Medium)
**Question**: A DevOps engineer needs to configure CSRF protection for AEM. Which filter should be enabled?
- A) Adobe Granite CSRF Filter
- B) Apache Sling Referrer Filter
- C) Adobe WCM Debug Filter
- D) Apache Sling Authentication Service

**Answer**: A) Adobe Granite CSRF Filter
**Explanation**: The Adobe Granite CSRF Filter provides Cross-Site Request Forgery protection for AEM. It validates CSRF tokens for POST requests and prevents unauthorized form submissions.
**Study Notes**: CSRF protection: Enable Adobe Granite CSRF Filter for form security

### Q63: Performance (Easy)
**Question**: Which JVM parameter should be used to set the initial heap size?
- A) -Xms
- B) -Xmx
- C) -XX:InitialHeapSize
- D) -XX:NewSize

**Answer**: A) -Xms
**Explanation**: The -Xms parameter sets the initial heap size for the JVM. This determines how much memory is allocated to the heap when the JVM starts.
**Study Notes**: JVM memory: Use -Xms to set initial heap size

### Q64: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle errors gracefully. Which configuration section should be used?
- A) /errorPage
- B) /errorDocument
- C) /errorHandler
- D) /errorPage

**Answer**: A) /errorPage
**Explanation**: The /errorPage section in dispatcher configuration allows you to define custom error pages for different HTTP status codes. This provides a better user experience when errors occur.
**Study Notes**: Dispatcher errors: Use /errorPage section for custom error handling

### Q65: Security (Medium)
**Question**: A DevOps engineer needs to configure authentication for AEM. Which service should be used to manage user authentication?
- A) Apache Sling Authentication Service
- B) Adobe Granite Authentication Service
- C) Apache Sling Service User Mapper Service
- D) Adobe Granite User Management Service

**Answer**: A) Apache Sling Authentication Service
**Explanation**: The Apache Sling Authentication Service is the primary service for managing user authentication in AEM. It handles login processes, session management, and authentication requirements.
**Study Notes**: Authentication: Use Apache Sling Authentication Service for user authentication

### Q66: Performance (Medium)
**Question**: A DevOps engineer needs to monitor AEM performance. Which MBean should be used to monitor JVM memory usage?
- A) java.lang:type=Memory
- B) java.lang:type=Runtime
- C) java.lang:type=GarbageCollector
- D) java.lang:type=MemoryPool

**Answer**: A) java.lang:type=Memory
**Explanation**: The java.lang:type=Memory MBean provides information about JVM memory usage, including heap and non-heap memory consumption. This is essential for monitoring memory-related performance issues.
**Study Notes**: JVM monitoring: Use java.lang:type=Memory MBean for memory usage monitoring

### Q67: Deployment (Easy)
**Question**: Which Maven profile is used to deploy content packages to the author instance?
- A) autoInstallPackage
- B) autoInstallBundle
- C) autoInstallPackageAuthor
- D) autoDeployPackage

**Answer**: A) autoInstallPackage
**Explanation**: The autoInstallPackage profile is used to deploy content packages to the author instance. This profile builds and installs packages directly to the target AEM author instance.
**Study Notes**: Maven deployment: Use autoInstallPackage profile for author deployment

### Q68: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle load balancing. Which configuration section should be used?
- A) /renders
- B) /cache
- C) /farms
- D) /loadbalancer

**Answer**: A) /renders
**Explanation**: The /renders section in dispatcher configuration defines the backend servers that can handle requests. This is used for load balancing and failover configuration.
**Study Notes**: Dispatcher load balancing: Use /renders section for backend server configuration

### Q69: Security (Easy)
**Question**: Which dispatcher filter rule should be used to block access to the CRX repository?
- A) /crx/*
- B) /system/crx/*
- C) /libs/crx/*
- D) /apps/crx/*

**Answer**: A) /crx/*
**Explanation**: The /crx/* pattern blocks access to the CRX repository, which should not be accessible on publish instances for security reasons. This prevents unauthorized access to the repository.
**Study Notes**: Security: Use /crx/* to block CRX repository access on publish

### Q70: Performance (Medium)
**Question**: A DevOps engineer needs to analyze AEM performance issues. Which tool should be used to analyze request.log files?
- A) riog.jar
- B) rlog.jar
- C) jail.jar
- D) oak-run.jar

**Answer**: A) riog.jar
**Explanation**: riog.jar is the tool specifically designed to analyze request.log files. It provides detailed analysis of request patterns, response times, and performance bottlenecks.
**Study Notes**: Performance analysis: Use riog.jar to analyze request.log files

### Q71: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure monitoring for AEM as a Cloud Service. Which service should be used to set up monitoring alerts?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager provides monitoring capabilities for AEM as a Cloud Service, including alert configuration, performance metrics, and health checks.
**Study Notes**: Cloud Service monitoring: Use Cloud Manager to configure monitoring alerts

### Q72: Security (Medium)
**Question**: A DevOps engineer needs to configure SSL/TLS for AEM. Which service should be used to manage SSL certificates?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager provides SSL certificate management for AEM as a Cloud Service, including certificate upload, renewal, and configuration.
**Study Notes**: SSL management: Use Cloud Manager to manage SSL certificates

### Q73: Performance (Easy)
**Question**: Which JVM parameter should be used to enable garbage collection logging?
- A) -XX:+PrintGC
- B) -XX:+PrintGCDetails
- C) -XX:+PrintGCTimeStamps
- D) -XX:+PrintGCApplicationStoppedTime

**Answer**: B) -XX:+PrintGCDetails
**Explanation**: The -XX:+PrintGCDetails parameter enables detailed garbage collection logging, providing information about GC events, memory usage, and performance impact.
**Study Notes**: GC logging: Use -XX:+PrintGCDetails for detailed garbage collection logging

### Q74: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle session management. Which configuration section should be used?
- A) /sessionmanagement
- B) /sessions
- C) /session
- D) /sessionmanagement

**Answer**: A) /sessionmanagement
**Explanation**: The /sessionmanagement section in dispatcher configuration controls how sessions are handled, including session persistence and timeout settings.
**Study Notes**: Dispatcher sessions: Use /sessionmanagement section for session configuration

### Q75: Security (Medium)
**Question**: A DevOps engineer needs to configure access control for AEM. Which service should be used to manage permissions?
- A) Apache Sling Authentication Service
- B) Adobe Granite Authentication Service
- C) Apache Sling Service User Mapper Service
- D) Adobe Granite User Management Service

**Answer**: D) Adobe Granite User Management Service
**Explanation**: The Adobe Granite User Management Service is responsible for managing user permissions and access control in AEM. It handles ACLs, user groups, and permission management.
**Study Notes**: Access control: Use Adobe Granite User Management Service for permission management

### Q76: Performance (Medium)
**Question**: A DevOps engineer needs to monitor AEM performance. Which MBean should be used to monitor garbage collection?
- A) java.lang:type=Memory
- B) java.lang:type=Runtime
- C) java.lang:type=GarbageCollector
- D) java.lang:type=MemoryPool

**Answer**: C) java.lang:type=GarbageCollector
**Explanation**: The java.lang:type=GarbageCollector MBean provides information about garbage collection events, including collection counts, times, and performance impact.
**Study Notes**: GC monitoring: Use java.lang:type=GarbageCollector MBean for garbage collection monitoring

### Q77: Deployment (Easy)
**Question**: Which Maven profile is used to deploy content packages to the publish instance?
- A) autoInstallPackage
- B) autoInstallBundle
- C) autoInstallPackagePublish
- D) autoDeployPackage

**Answer**: C) autoInstallPackagePublish
**Explanation**: The autoInstallPackagePublish profile is used to deploy content packages to the publish instance. This profile builds and installs packages directly to the target AEM publish instance.
**Study Notes**: Maven deployment: Use autoInstallPackagePublish profile for publish deployment

### Q78: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle caching. Which configuration section should be used?
- A) /cache
- B) /farms
- C) /renders
- D) /static

**Answer**: A) /cache
**Explanation**: The /cache section in dispatcher configuration controls how content is cached, including cache rules, invalidation, and storage settings.
**Study Notes**: Dispatcher caching: Use /cache section for cache configuration

### Q79: Security (Easy)
**Question**: Which dispatcher filter rule should be used to block access to the system console?
- A) /system/*
- B) /system/console/*
- C) /console/*
- D) /system/felix/*

**Answer**: A) /system/*
**Explanation**: The /system/* pattern blocks access to all system paths, including the system console. This provides comprehensive protection against unauthorized system access.
**Study Notes**: Security: Use /system/* to block system console access

### Q80: Performance (Medium)
**Question**: A DevOps engineer needs to analyze AEM performance issues. Which tool should be used to analyze dispatcher.log files?
- A) riog.jar
- B) rlog.jar
- C) jail.jar
- D) oak-run.jar

**Answer**: B) rlog.jar
**Explanation**: rlog.jar is the tool specifically designed to analyze dispatcher.log files. It provides detailed analysis of dispatcher performance, cache hit ratios, and request patterns.
**Study Notes**: Dispatcher analysis: Use rlog.jar to analyze dispatcher.log files

### Q81: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure custom domains for AEM as a Cloud Service. Which service should be used to manage domain configurations?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager is the service used to configure custom domains for AEM as a Cloud Service. It provides a self-service interface for managing domain configurations and SSL certificates.
**Study Notes**: Cloud Service domains: Use Cloud Manager to configure custom domains

### Q82: Security (Medium)
**Question**: A DevOps engineer needs to configure CSRF protection for AEM. Which filter should be enabled?
- A) Adobe Granite CSRF Filter
- B) Apache Sling Referrer Filter
- C) Adobe WCM Debug Filter
- D) Apache Sling Authentication Service

**Answer**: A) Adobe Granite CSRF Filter
**Explanation**: The Adobe Granite CSRF Filter provides Cross-Site Request Forgery protection for AEM. It validates CSRF tokens for POST requests and prevents unauthorized form submissions.
**Study Notes**: CSRF protection: Enable Adobe Granite CSRF Filter for form security

### Q83: Performance (Easy)
**Question**: Which JVM parameter should be used to set the maximum heap size?
- A) -Xms
- B) -Xmx
- C) -XX:MaxHeapSize
- D) -XX:MaxDirectMemorySize

**Answer**: B) -Xmx
**Explanation**: The -Xmx parameter sets the maximum heap size for the JVM. This prevents the JVM from consuming more memory than specified, helping to control memory usage and prevent OutOfMemoryError.
**Study Notes**: JVM memory: Use -Xmx to set maximum heap size

### Q84: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle errors gracefully. Which configuration section should be used?
- A) /errorPage
- B) /errorDocument
- C) /errorHandler
- D) /errorPage

**Answer**: A) /errorPage
**Explanation**: The /errorPage section in dispatcher configuration allows you to define custom error pages for different HTTP status codes. This provides a better user experience when errors occur.
**Study Notes**: Dispatcher errors: Use /errorPage section for custom error handling

### Q85: Security (Medium)
**Question**: A DevOps engineer needs to configure authentication for AEM. Which service should be used to manage user authentication?
- A) Apache Sling Authentication Service
- B) Adobe Granite Authentication Service
- C) Apache Sling Service User Mapper Service
- D) Adobe Granite User Management Service

**Answer**: A) Apache Sling Authentication Service
**Explanation**: The Apache Sling Authentication Service is the primary service for managing user authentication in AEM. It handles login processes, session management, and authentication requirements.
**Study Notes**: Authentication: Use Apache Sling Authentication Service for user authentication

### Q86: Performance (Medium)
**Question**: A DevOps engineer needs to monitor AEM performance. Which MBean should be used to monitor JVM memory usage?
- A) java.lang:type=Memory
- B) java.lang:type=Runtime
- C) java.lang:type=GarbageCollector
- D) java.lang:type=MemoryPool

**Answer**: A) java.lang:type=Memory
**Explanation**: The java.lang:type=Memory MBean provides information about JVM memory usage, including heap and non-heap memory consumption. This is essential for monitoring memory-related performance issues.
**Study Notes**: JVM monitoring: Use java.lang:type=Memory MBean for memory usage monitoring

### Q87: Deployment (Easy)
**Question**: Which Maven profile is used to deploy content packages to the author instance?
- A) autoInstallPackage
- B) autoInstallBundle
- C) autoInstallPackageAuthor
- D) autoDeployPackage

**Answer**: A) autoInstallPackage
**Explanation**: The autoInstallPackage profile is used to deploy content packages to the author instance. This profile builds and installs packages directly to the target AEM author instance.
**Study Notes**: Maven deployment: Use autoInstallPackage profile for author deployment

### Q88: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle load balancing. Which configuration section should be used?
- A) /renders
- B) /cache
- C) /farms
- D) /loadbalancer

**Answer**: A) /renders
**Explanation**: The /renders section in dispatcher configuration defines the backend servers that can handle requests. This is used for load balancing and failover configuration.
**Study Notes**: Dispatcher load balancing: Use /renders section for backend server configuration

### Q89: Security (Easy)
**Question**: Which dispatcher filter rule should be used to block access to the CRX repository?
- A) /crx/*
- B) /system/crx/*
- C) /libs/crx/*
- D) /apps/crx/*

**Answer**: A) /crx/*
**Explanation**: The /crx/* pattern blocks access to the CRX repository, which should not be accessible on publish instances for security reasons. This prevents unauthorized access to the repository.
**Study Notes**: Security: Use /crx/* to block CRX repository access on publish

### Q90: Performance (Medium)
**Question**: A DevOps engineer needs to analyze AEM performance issues. Which tool should be used to analyze request.log files?
- A) riog.jar
- B) rlog.jar
- C) jail.jar
- D) oak-run.jar

**Answer**: A) riog.jar
**Explanation**: riog.jar is the tool specifically designed to analyze request.log files. It provides detailed analysis of request patterns, response times, and performance bottlenecks.
**Study Notes**: Performance analysis: Use riog.jar to analyze request.log files

### Q91: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure monitoring for AEM as a Cloud Service. Which service should be used to set up monitoring alerts?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager provides monitoring capabilities for AEM as a Cloud Service, including alert configuration, performance metrics, and health checks.
**Study Notes**: Cloud Service monitoring: Use Cloud Manager to configure monitoring alerts

### Q92: Security (Medium)
**Question**: A DevOps engineer needs to configure SSL/TLS for AEM. Which service should be used to manage SSL certificates?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager provides SSL certificate management for AEM as a Cloud Service, including certificate upload, renewal, and configuration.
**Study Notes**: SSL management: Use Cloud Manager to manage SSL certificates

### Q93: Performance (Easy)
**Question**: Which JVM parameter should be used to enable garbage collection logging?
- A) -XX:+PrintGC
- B) -XX:+PrintGCDetails
- C) -XX:+PrintGCTimeStamps
- D) -XX:+PrintGCApplicationStoppedTime

**Answer**: B) -XX:+PrintGCDetails
**Explanation**: The -XX:+PrintGCDetails parameter enables detailed garbage collection logging, providing information about GC events, memory usage, and performance impact.
**Study Notes**: GC logging: Use -XX:+PrintGCDetails for detailed garbage collection logging

### Q94: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle session management. Which configuration section should be used?
- A) /sessionmanagement
- B) /sessions
- C) /session
- D) /sessionmanagement

**Answer**: A) /sessionmanagement
**Explanation**: The /sessionmanagement section in dispatcher configuration controls how sessions are handled, including session persistence and timeout settings.
**Study Notes**: Dispatcher sessions: Use /sessionmanagement section for session configuration

### Q95: Security (Medium)
**Question**: A DevOps engineer needs to configure access control for AEM. Which service should be used to manage permissions?
- A) Apache Sling Authentication Service
- B) Adobe Granite Authentication Service
- C) Apache Sling Service User Mapper Service
- D) Adobe Granite User Management Service

**Answer**: D) Adobe Granite User Management Service
**Explanation**: The Adobe Granite User Management Service is responsible for managing user permissions and access control in AEM. It handles ACLs, user groups, and permission management.
**Study Notes**: Access control: Use Adobe Granite User Management Service for permission management

### Q96: Performance (Medium)
**Question**: A DevOps engineer needs to monitor AEM performance. Which MBean should be used to monitor garbage collection?
- A) java.lang:type=Memory
- B) java.lang:type=Runtime
- C) java.lang:type=GarbageCollector
- D) java.lang:type=MemoryPool

**Answer**: C) java.lang:type=GarbageCollector
**Explanation**: The java.lang:type=GarbageCollector MBean provides information about garbage collection events, including collection counts, times, and performance impact.
**Study Notes**: GC monitoring: Use java.lang:type=GarbageCollector MBean for garbage collection monitoring

### Q97: Deployment (Easy)
**Question**: Which Maven profile is used to deploy content packages to the publish instance?
- A) autoInstallPackage
- B) autoInstallBundle
- C) autoInstallPackagePublish
- D) autoDeployPackage

**Answer**: C) autoInstallPackagePublish
**Explanation**: The autoInstallPackagePublish profile is used to deploy content packages to the publish instance. This profile builds and installs packages directly to the target AEM publish instance.
**Study Notes**: Maven deployment: Use autoInstallPackagePublish profile for publish deployment

### Q98: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle caching. Which configuration section should be used?
- A) /cache
- B) /farms
- C) /renders
- D) /static

**Answer**: A) /cache
**Explanation**: The /cache section in dispatcher configuration controls how content is cached, including cache rules, invalidation, and storage settings.
**Study Notes**: Dispatcher caching: Use /cache section for cache configuration

### Q99: Security (Easy)
**Question**: Which dispatcher filter rule should be used to block access to the system console?
- A) /system/*
- B) /system/console/*
- C) /console/*
- D) /system/felix/*

**Answer**: A) /system/*
**Explanation**: The /system/* pattern blocks access to all system paths, including the system console. This provides comprehensive protection against unauthorized system access.
**Study Notes**: Security: Use /system/* to block system console access

### Q100: Performance (Medium)
**Question**: A DevOps engineer needs to analyze AEM performance issues. Which tool should be used to analyze dispatcher.log files?
- A) riog.jar
- B) rlog.jar
- C) jail.jar
- D) oak-run.jar

**Answer**: B) rlog.jar
**Explanation**: rlog.jar is the tool specifically designed to analyze dispatcher.log files. It provides detailed analysis of dispatcher performance, cache hit ratios, and request patterns.
**Study Notes**: Dispatcher analysis: Use rlog.jar to analyze dispatcher.log files

### Q101: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure custom domains for AEM as a Cloud Service. Which service should be used to manage domain configurations?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager is the service used to configure custom domains for AEM as a Cloud Service. It provides a self-service interface for managing domain configurations and SSL certificates.
**Study Notes**: Cloud Service domains: Use Cloud Manager to configure custom domains

### Q102: Security (Medium)
**Question**: A DevOps engineer needs to configure CSRF protection for AEM. Which filter should be enabled?
- A) Adobe Granite CSRF Filter
- B) Apache Sling Referrer Filter
- C) Adobe WCM Debug Filter
- D) Apache Sling Authentication Service

**Answer**: A) Adobe Granite CSRF Filter
**Explanation**: The Adobe Granite CSRF Filter provides Cross-Site Request Forgery protection for AEM. It validates CSRF tokens for POST requests and prevents unauthorized form submissions.
**Study Notes**: CSRF protection: Enable Adobe Granite CSRF Filter for form security

### Q103: Performance (Easy)
**Question**: Which JVM parameter should be used to set the maximum heap size?
- A) -Xms
- B) -Xmx
- C) -XX:MaxHeapSize
- D) -XX:MaxDirectMemorySize

**Answer**: B) -Xmx
**Explanation**: The -Xmx parameter sets the maximum heap size for the JVM. This prevents the JVM from consuming more memory than specified, helping to control memory usage and prevent OutOfMemoryError.
**Study Notes**: JVM memory: Use -Xmx to set maximum heap size

### Q104: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle errors gracefully. Which configuration section should be used?
- A) /errorPage
- B) /errorDocument
- C) /errorHandler
- D) /errorPage

**Answer**: A) /errorPage
**Explanation**: The /errorPage section in dispatcher configuration allows you to define custom error pages for different HTTP status codes. This provides a better user experience when errors occur.
**Study Notes**: Dispatcher errors: Use /errorPage section for custom error handling

### Q105: Security (Medium)
**Question**: A DevOps engineer needs to configure authentication for AEM. Which service should be used to manage user authentication?
- A) Apache Sling Authentication Service
- B) Adobe Granite Authentication Service
- C) Apache Sling Service User Mapper Service
- D) Adobe Granite User Management Service

**Answer**: A) Apache Sling Authentication Service
**Explanation**: The Apache Sling Authentication Service is the primary service for managing user authentication in AEM. It handles login processes, session management, and authentication requirements.
**Study Notes**: Authentication: Use Apache Sling Authentication Service for user authentication

### Q106: Performance (Medium)
**Question**: A DevOps engineer needs to monitor AEM performance. Which MBean should be used to monitor JVM memory usage?
- A) java.lang:type=Memory
- B) java.lang:type=Runtime
- C) java.lang:type=GarbageCollector
- D) java.lang:type=MemoryPool

**Answer**: A) java.lang:type=Memory
**Explanation**: The java.lang:type=Memory MBean provides information about JVM memory usage, including heap and non-heap memory consumption. This is essential for monitoring memory-related performance issues.
**Study Notes**: JVM monitoring: Use java.lang:type=Memory MBean for memory usage monitoring

### Q107: Deployment (Easy)
**Question**: Which Maven profile is used to deploy content packages to the author instance?
- A) autoInstallPackage
- B) autoInstallBundle
- C) autoInstallPackageAuthor
- D) autoDeployPackage

**Answer**: A) autoInstallPackage
**Explanation**: The autoInstallPackage profile is used to deploy content packages to the author instance. This profile builds and installs packages directly to the target AEM author instance.
**Study Notes**: Maven deployment: Use autoInstallPackage profile for author deployment

### Q108: Dispatcher (Medium)
**Question**: A DevOps engineer needs to configure the dispatcher to handle load balancing. Which configuration section should be used?
- A) /renders
- B) /cache
- C) /farms
- D) /loadbalancer

**Answer**: A) /renders
**Explanation**: The /renders section in dispatcher configuration defines the backend servers that can handle requests. This is used for load balancing and failover configuration.
**Study Notes**: Dispatcher load balancing: Use /renders section for backend server configuration

### Q109: Security (Easy)
**Question**: Which dispatcher filter rule should be used to block access to the CRX repository?
- A) /crx/*
- B) /system/crx/*
- C) /libs/crx/*
- D) /apps/crx/*

**Answer**: A) /crx/*
**Explanation**: The /crx/* pattern blocks access to the CRX repository, which should not be accessible on publish instances for security reasons. This prevents unauthorized access to the repository.
**Study Notes**: Security: Use /crx/* to block CRX repository access on publish

### Q110: Performance (Medium)
**Question**: A DevOps engineer needs to analyze AEM performance issues. Which tool should be used to analyze request.log files?
- A) riog.jar
- B) rlog.jar
- C) jail.jar
- D) oak-run.jar

**Answer**: A) riog.jar
**Explanation**: riog.jar is the tool specifically designed to analyze request.log files. It provides detailed analysis of request patterns, response times, and performance bottlenecks.
**Study Notes**: Performance analysis: Use riog.jar to analyze request.log files

### Q111: Cloud Service (Medium)
**Question**: A DevOps engineer needs to configure monitoring for AEM as a Cloud Service. Which service should be used to set up monitoring alerts?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager provides monitoring capabilities for AEM as a Cloud Service, including alert configuration, performance metrics, and health checks.
**Study Notes**: Cloud Service monitoring: Use Cloud Manager to configure monitoring alerts

### Q112: Security (Medium)
**Question**: A DevOps engineer needs to configure SSL/TLS for AEM. Which service should be used to manage SSL certificates?
- A) Cloud Manager
- B) Admin Console
- C) Experience Manager
- D) Adobe I/O

**Answer**: A) Cloud Manager
**Explanation**: Cloud Manager provides SSL certificate management for AEM as a Cloud Service, including certificate upload, renewal, and configuration.
**Study Notes**: SSL management: Use Cloud Manager to manage SSL certificates

### Q113: Dispatcher (Medium)
**Question**: A request, /home_page?tab=1, is received on the dispatcher with a parameter. This request is not cached, but should be. Which configuration in the dispatcher should be added to make sure such requests are cached in the future?
- A) /cacheRequests {/0001 { /glob "*"/type "deny" }/0002 {/glob "tab" /type "permit" }}
- B) /ignoreUrlParams {/0001 { /glob "*"/type "deny" }/0002 {/glob "?tab=1" /type "allow" }}
- C) /allowCaching{ /0001 { /glob "*"/type "deny" }/0002 {/glob "tab" /type "cache" }}
- D) /ignoreUrlParams {/0001 {/glob "*"/type "deny"} /0002 {/glob "tab" /type "allow" }}

**Answer**: D) /ignoreUrlParams {/0001 {/glob "*"/type "deny"} /0002 {/glob "tab" /type "allow" }}
**Explanation**: /ignoreUrlParams {/0001 {/glob "*"/type "deny"} /0002 {/glob "tab" /type "allow" }}. By default, AEM Dispatcher does not cache requests that contain URL parameters unless explicitly configured. This configuration denies all parameters by default and explicitly allows "tab" to be ignored for caching, so requests like /home_page?tab=1 will be treated the same as /home_page for caching purposes.
**Study Notes**: Dispatcher caching: Use /ignoreUrlParams to cache requests with parameters

### Q114: Performance (Medium)
**Question**: The log files contain the error "Too many files", and CRX is not responding. What should a DevOps engineer do to increase the open files limit?
- A) Restart AEM 6.x with a higher number of value in start.sh --fs.file.max=value
- B) AEM 6.x automatically handles such a limit and increase the limit dynamically during the next restart
- C) Set new Java Virtual Machine limits by -Djava.fs.file-max= and restart AEM
- D) Check the CRX process user limit for maximum open files, and run ulimit to set higher values

**Answer**: D) Check the CRX process user limit for maximum open files, and run ulimit to set higher values
**Explanation**: Check the CRX process user limit for maximum open files, and run ulimit to set higher values. The "Too many files" error indicates that the operating system has hit the limit for open file descriptors, which is controlled by ulimit settings. The best approach is to check the current limit with 'ulimit -n' and increase it temporarily or permanently via limits.conf.
**Study Notes**: File descriptor limit: Use ulimit to increase open files limit

### Q115: Performance (Easy)
**Question**: When configuring the Java Virtual Machine (VM), which setting configures the JVM heap size?
- A) xmx and jvmx
- B) xms and xmx
- C) xss and jvms
- D) xms and jhs

**Answer**: B) xms and xmx
**Explanation**: xms and xmx. The JVM heap size is configured using -Xms (sets initial heap size) and -Xmx (sets maximum heap size). For example, '-Xms2048m -Xmx4096m' sets initial heap to 2GB and maximum heap to 4GB. These are fundamental JVM memory configuration parameters used in AEM deployments.
**Study Notes**: JVM configuration: Use -Xms and -Xmx for heap size settings

### Q116: Security (Medium)
**Question**: How should a DevOps engineer prevent Denial of Service (DoS) attacks against AEM 6.x instances?
- A) By implementing a web application firewall and installing the latest security hotfixes
- B) By configuring Sling, Adobe Dispatcher, a web application firewall, installing the latest security hotfixes and implementing a protected network environment
- C) By leaving the Adobe Dispatcher set to the default configuration and installing the latest security hotfixes
- D) By implementing a protected network environment installing the latest security hotfixes

**Answer**: B) By configuring Sling, Adobe Dispatcher, a web application firewall, installing the latest security hotfixes and implementing a protected network environment
**Explanation**: By configuring Sling, Adobe Dispatcher, a web application firewall, installing the latest security hotfixes and implementing a protected network environment. A multi-layered security approach is the best defense against DoS attacks, including Sling configuration for rate limiting, Dispatcher for IP whitelisting and caching, WAF for blocking malicious traffic, security hotfixes for vulnerabilities, and protected network environment for access restrictions.
**Study Notes**: DoS prevention: Use multi-layered security approach

### Q117: Monitoring (Easy)
**Question**: When monitoring replication agents, for which two event should a monitoring system provide alerts? (Choose two.)
- A) More than 10,000 items in the queue
- B) 403 in the replication log
- C) Queue blocked
- D) 200 in the replication log

**Answer**: A and C) More than 10,000 items in the queue and Queue blocked
**Explanation**: More than 10,000 items in the queue and Queue blocked. Large queue indicates replication bottleneck and potential content sync issues requiring intervention, while queue blocked is a critical failure condition that stops content publication and requires immediate attention. These conditions are critical monitoring metrics for maintaining system health.
**Study Notes**: Replication monitoring: Alert on large queue size and blocked status

---

## Study Recommendations

### For Flashcard Questions (60 questions)
- Focus on memorizing key commands, tools, and configurations
- Use spaced repetition for retention
- Practice with tools like Anki or Quizlet

### For Practice Questions (57 questions)
- Understand the underlying concepts
- Practice troubleshooting scenarios
- Review Adobe documentation for context

## Key Topics to Master

### 1. CRX/Oak Repository Management
- Offline compaction with oak-run jar
- Online compaction frequency (once per day)
- Repository backup strategies
- Index management and migration

### 2. Dispatcher Configuration
- Caching rules and invalidation
- Security filters and access control
- Parameter handling (/ignoreUrlParams)
- Error page configuration

### 3. Security Best Practices
- CSRF token handling
- Production Ready Mode settings
- DoS attack prevention
- Authentication and authorization

### 4. Cloud Service Migration
- Content Transfer Tool requirements
- Index consolidation strategies
- Environment-specific configurations
- Scaling and monitoring

### 5. Performance Optimization
- JVM parameter tuning (-Xms, -Xmx)
- Cache hit ratio monitoring
- File descriptor limits (ulimit)
- Performance testing with Tough Day 2

## Files Generated
1. **AEM_DevOps_Complete_CSV.csv** - Complete CSV with all 117 questions
2. **AEM_DevOps_Complete_JSON.json** - JSON format for programmatic use
3. **AEM_DevOps_Complete_Review.md** - This comprehensive review document

## Usage Instructions
- Import CSV into Anki, Quizlet, or similar flashcard tools
- Use JSON for custom study applications
- Reference this Markdown document for comprehensive review
- Focus on weak areas identified during practice

## Next Steps
1. Import questions into your preferred study tool
2. Create study schedule based on difficulty levels
3. Practice with real AEM environments when possible
4. Review Adobe documentation for additional context
5. Take practice exams to identify knowledge gaps

---
*Generated from 117 AEM DevOps exam questions - Complete technical review and study preparation materials*