# node and process steps

adalah plugin yang secara default sudah terinstall bila sudah menginstall plugin jenkins pipeline, plugin ini digunakan untuk menjalankan / mengeksekusi perintah terminal, seperti shell script (unix), atau command script (windows)

dokumentasi penggunaan perintahnya dapat dilihat disini

[https://www.jenkins.io/doc/pipeline/steps/workflow-durable-task-step/](https://www.jenkins.io/doc/pipeline/steps/workflow-durable-task-step/)

## contoh

Jenkinsfile

menggunakan perintah sh untuk mengeksekusi shell script

```bash
pipeline {
    agent {
        node {
            label "22.04 && singapore"
        }
    }

    stages {

        stage("build") {
            steps {
                sh("./mvnw clean compile test-compile")
            }
        }

        stage("test") {
            steps {
                sh("./mvnw test")
            }
        }

    }
}
```

stage view:

![Untitled](node%20and%20process%20steps%2088f99d57fec3446e827da32a5e232b28/Untitled.png)

console output:

```bash
Started by user Reiya Tenggara
Obtained Jenkinsfile from git git@github.com:Reiya24/belajar-jenkins-pipeline.git
[Pipeline] Start of Pipeline
[Pipeline] node
Running on agent1 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential reiya24
Fetching changes from the remote Git repository
 > git rev-parse --resolve-git-dir /home/reiya24/jenkins_agent1/workspace/belajar pipeline/.git # timeout=10
 > git config remote.origin.url git@github.com:Reiya24/belajar-jenkins-pipeline.git # timeout=10
Fetching upstream changes from git@github.com:Reiya24/belajar-jenkins-pipeline.git
 > git --version # timeout=10
 > git --version # 'git version 2.34.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file, will automatically accept unseen keys
 > git fetch --tags --force --progress -- git@github.com:Reiya24/belajar-jenkins-pipeline.git +refs/heads/*:refs/remotes/origin/* # timeout=10
Checking out Revision 0c2fe82ca03447a0b1e701ab7a9f55c17470fdce (origin/main)
Commit message: "Update Jenkinsfile"
 > git rev-parse origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 0c2fe82ca03447a0b1e701ab7a9f55c17470fdce # timeout=10
 > git rev-list --no-walk 0c2fe82ca03447a0b1e701ab7a9f55c17470fdce # timeout=10
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (build)
[Pipeline] sh
+ ./mvnw clean compile test-compile
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------< programmer-zaman-now:belajar-spring-dasar >--------------
[INFO] Building belajar-spring-dasar 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ belajar-spring-dasar ---
[INFO] Deleting /home/reiya24/jenkins_agent1/workspace/belajar pipeline/target
[INFO] 
[INFO] --- maven-resources-plugin:3.2.0:resources (default-resources) @ belajar-spring-dasar ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Using 'UTF-8' encoding to copy filtered properties files.
[INFO] Copying 1 resource
[INFO] Copying 1 resource
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ belajar-spring-dasar ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 58 source files to /home/reiya24/jenkins_agent1/workspace/belajar pipeline/target/classes
[INFO] 
[INFO] --- maven-resources-plugin:3.2.0:resources (default-resources) @ belajar-spring-dasar ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Using 'UTF-8' encoding to copy filtered properties files.
[INFO] Copying 1 resource
[INFO] Copying 1 resource
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ belajar-spring-dasar ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 58 source files to /home/reiya24/jenkins_agent1/workspace/belajar pipeline/target/classes
[INFO] 
[INFO] --- maven-resources-plugin:3.2.0:testResources (default-testResources) @ belajar-spring-dasar ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Using 'UTF-8' encoding to copy filtered properties files.
[INFO] skip non existing resourceDirectory /home/reiya24/jenkins_agent1/workspace/belajar pipeline/src/test/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:testCompile (default-testCompile) @ belajar-spring-dasar ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 25 source files to /home/reiya24/jenkins_agent1/workspace/belajar pipeline/target/test-classes
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  16.320 s
[INFO] Finished at: 2023-01-28T13:56:54Z
[INFO] ------------------------------------------------------------------------
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (test)
[Pipeline] sh
+ ./mvnw test
[INFO] Scanning for projects...
[INFO] 
[INFO] -------------< programmer-zaman-now:belajar-spring-dasar >--------------
[INFO] Building belajar-spring-dasar 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-resources-plugin:3.2.0:resources (default-resources) @ belajar-spring-dasar ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Using 'UTF-8' encoding to copy filtered properties files.
[INFO] Copying 1 resource
[INFO] Copying 1 resource
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ belajar-spring-dasar ---
[INFO] Nothing to compile - all classes are up to date
[INFO] 
[INFO] --- maven-resources-plugin:3.2.0:testResources (default-testResources) @ belajar-spring-dasar ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Using 'UTF-8' encoding to copy filtered properties files.
[INFO] skip non existing resourceDirectory /home/reiya24/jenkins_agent1/workspace/belajar pipeline/src/test/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:testCompile (default-testCompile) @ belajar-spring-dasar ---
[INFO] Nothing to compile - all classes are up to date
[INFO] 
[INFO] --- maven-surefire-plugin:2.22.2:test (default-test) @ belajar-spring-dasar ---
[INFO] 
[INFO] -------------------------------------------------------
[INFO]  T E S T S
[INFO] -------------------------------------------------------
[INFO] Running programmerzamannow.spring.core.application.FooApplicationTest
13:57:10.879 [main] DEBUG org.springframework.test.context.BootstrapUtils - Instantiating CacheAwareContextLoaderDelegate from class [org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate]
13:57:10.901 [main] DEBUG org.springframework.test.context.BootstrapUtils - Instantiating BootstrapContext using constructor [public org.springframework.test.context.support.DefaultBootstrapContext(java.lang.Class,org.springframework.test.context.CacheAwareContextLoaderDelegate)]
13:57:10.975 [main] DEBUG org.springframework.test.context.BootstrapUtils - Instantiating TestContextBootstrapper for test class [programmerzamannow.spring.core.application.FooApplicationTest] from class [org.springframework.boot.test.context.SpringBootTestContextBootstrapper]
13:57:10.998 [main] INFO org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Neither @ContextConfiguration nor @ContextHierarchy found for test class [programmerzamannow.spring.core.application.FooApplicationTest], using SpringBootContextLoader
13:57:11.012 [main] DEBUG org.springframework.test.context.support.AbstractContextLoader - Did not detect default resource location for test class [programmerzamannow.spring.core.application.FooApplicationTest]: class path resource [programmerzamannow/spring/core/application/FooApplicationTest-context.xml] does not exist
13:57:11.014 [main] DEBUG org.springframework.test.context.support.AbstractContextLoader - Did not detect default resource location for test class [programmerzamannow.spring.core.application.FooApplicationTest]: class path resource [programmerzamannow/spring/core/application/FooApplicationTestContext.groovy] does not exist
13:57:11.015 [main] INFO org.springframework.test.context.support.AbstractContextLoader - Could not detect default resource locations for test class [programmerzamannow.spring.core.application.FooApplicationTest]: no resource found for suffixes {-context.xml, Context.groovy}.
13:57:11.187 [main] DEBUG org.springframework.test.context.support.ActiveProfilesUtils - Could not find an 'annotation declaring class' for annotation type [org.springframework.test.context.ActiveProfiles] and class [programmerzamannow.spring.core.application.FooApplicationTest]
13:57:11.530 [main] DEBUG org.springframework.boot.test.context.SpringBootTestContextBootstrapper - @TestExecutionListeners is not present for class [programmerzamannow.spring.core.application.FooApplicationTest]: using defaults.
13:57:11.533 [main] INFO org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Loaded default TestExecutionListener class names from location [META-INF/spring.factories]: [org.springframework.boot.test.mock.mockito.MockitoTestExecutionListener, org.springframework.boot.test.mock.mockito.ResetMocksTestExecutionListener, org.springframework.boot.test.autoconfigure.restdocs.RestDocsTestExecutionListener, org.springframework.boot.test.autoconfigure.web.client.MockRestServiceServerResetTestExecutionListener, org.springframework.boot.test.autoconfigure.web.servlet.MockMvcPrintOnlyOnFailureTestExecutionListener, org.springframework.boot.test.autoconfigure.web.servlet.WebDriverTestExecutionListener, org.springframework.boot.test.autoconfigure.webservices.client.MockWebServiceServerTestExecutionListener, org.springframework.test.context.web.ServletTestExecutionListener, org.springframework.test.context.support.DirtiesContextBeforeModesTestExecutionListener, org.springframework.test.context.event.ApplicationEventsTestExecutionListener, org.springframework.test.context.support.DependencyInjectionTestExecutionListener, org.springframework.test.context.support.DirtiesContextTestExecutionListener, org.springframework.test.context.transaction.TransactionalTestExecutionListener, org.springframework.test.context.jdbc.SqlScriptsTestExecutionListener, org.springframework.test.context.event.EventPublishingTestExecutionListener]
13:57:11.559 [main] DEBUG org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Skipping candidate TestExecutionListener [org.springframework.test.context.web.ServletTestExecutionListener] due to a missing dependency. Specify custom listener classes or make the default listener classes and their required dependencies available. Offending class: [javax/servlet/ServletContext]
13:57:11.562 [main] DEBUG org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Skipping candidate TestExecutionListener [org.springframework.test.context.transaction.TransactionalTestExecutionListener] due to a missing dependency. Specify custom listener classes or make the default listener classes and their required dependencies available. Offending class: [org/springframework/transaction/interceptor/TransactionAttributeSource]
13:57:11.562 [main] DEBUG org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Skipping candidate TestExecutionListener [org.springframework.test.context.jdbc.SqlScriptsTestExecutionListener] due to a missing dependency. Specify custom listener classes or make the default listener classes and their required dependencies available. Offending class: [org/springframework/transaction/interceptor/TransactionAttribute]
13:57:11.564 [main] INFO org.springframework.boot.test.context.SpringBootTestContextBootstrapper - Using TestExecutionListeners: [org.springframework.test.context.support.DirtiesContextBeforeModesTestExecutionListener@3ddc6915, org.springframework.test.context.event.ApplicationEventsTestExecutionListener@704deff2, org.springframework.boot.test.mock.mockito.MockitoTestExecutionListener@379614be, org.springframework.boot.test.autoconfigure.SpringBootDependencyInjectionTestExecutionListener@404bbcbd, org.springframework.test.context.support.DirtiesContextTestExecutionListener@1e81f160, org.springframework.test.context.event.EventPublishingTestExecutionListener@1acaf3d, org.springframework.boot.test.mock.mockito.ResetMocksTestExecutionListener@6986852, org.springframework.boot.test.autoconfigure.restdocs.RestDocsTestExecutionListener@1bab8268, org.springframework.boot.test.autoconfigure.web.client.MockRestServiceServerResetTestExecutionListener@a307a8c, org.springframework.boot.test.autoconfigure.web.servlet.MockMvcPrintOnlyOnFailureTestExecutionListener@6e01f9b0, org.springframework.boot.test.autoconfigure.web.servlet.WebDriverTestExecutionListener@2b9ed6da, org.springframework.boot.test.autoconfigure.webservices.client.MockWebServiceServerTestExecutionListener@6c61a903]
13:57:11.575 [main] DEBUG org.springframework.test.context.support.AbstractDirtiesContextTestExecutionListener - Before test class: context [DefaultTestContext@68f1b17f testClass = FooApplicationTest, testInstance = [null], testMethod = [null], testException = [null], mergedContextConfiguration = [MergedContextConfiguration@1722011b testClass = FooApplicationTest, locations = '{}', classes = '{class programmerzamannow.spring.core.application.FooApplication}', contextInitializerClasses = '[]', activeProfiles = '{}', propertySourceLocations = '{}', propertySourceProperties = '{org.springframework.boot.test.context.SpringBootTestContextBootstrapper=true}', contextCustomizers = set[org.springframework.boot.test.context.filter.ExcludeFilterContextCustomizer@a2431d0, org.springframework.boot.test.json.DuplicateJsonObjectContextCustomizerFactory$DuplicateJsonObjectContextCustomizer@1b6e1eff, org.springframework.boot.test.mock.mockito.MockitoContextCustomizer@0, org.springframework.boot.test.web.client.TestRestTemplateContextCustomizer@793be5ca, org.springframework.boot.test.autoconfigure.actuate.metrics.MetricsExportContextCustomizerFactory$DisableMetricExportContextCustomizer@24fcf36f, org.springframework.boot.test.autoconfigure.properties.PropertyMappingContextCustomizer@0, org.springframework.boot.test.autoconfigure.web.servlet.WebDriverContextCustomizerFactory$Customizer@fa49800, org.springframework.boot.test.context.SpringBootTestArgs@1, org.springframework.boot.test.context.SpringBootTestWebEnvironment@26aa12dd], contextLoader = 'org.springframework.boot.test.context.SpringBootContextLoader', parent = [null]], attributes = map[[empty]]], class annotated with @DirtiesContext [false] with mode [null].
13:57:11.613 [main] DEBUG org.springframework.test.context.support.DependencyInjectionTestExecutionListener - Performing dependency injection for test context [[DefaultTestContext@68f1b17f testClass = FooApplicationTest, testInstance = programmerzamannow.spring.core.application.FooApplicationTest@327af41b, testMethod = [null], testException = [null], mergedContextConfiguration = [MergedContextConfiguration@1722011b testClass = FooApplicationTest, locations = '{}', classes = '{class programmerzamannow.spring.core.application.FooApplication}', contextInitializerClasses = '[]', activeProfiles = '{}', propertySourceLocations = '{}', propertySourceProperties = '{org.springframework.boot.test.context.SpringBootTestContextBootstrapper=true}', contextCustomizers = set[org.springframework.boot.test.context.filter.ExcludeFilterContextCustomizer@a2431d0, org.springframework.boot.test.json.DuplicateJsonObjectContextCustomizerFactory$DuplicateJsonObjectContextCustomizer@1b6e1eff, org.springframework.boot.test.mock.mockito.MockitoContextCustomizer@0, org.springframework.boot.test.web.client.TestRestTemplateContextCustomizer@793be5ca, org.springframework.boot.test.autoconfigure.actuate.metrics.MetricsExportContextCustomizerFactory$DisableMetricExportContextCustomizer@24fcf36f, org.springframework.boot.test.autoconfigure.properties.PropertyMappingContextCustomizer@0, org.springframework.boot.test.autoconfigure.web.servlet.WebDriverContextCustomizerFactory$Customizer@fa49800, org.springframework.boot.test.context.SpringBootTestArgs@1, org.springframework.boot.test.context.SpringBootTestWebEnvironment@26aa12dd], contextLoader = 'org.springframework.boot.test.context.SpringBootContextLoader', parent = [null]], attributes = map['org.springframework.test.context.event.ApplicationEventsTestExecutionListener.recordApplicationEvents' -> false]]].
13:57:11.667 [main] DEBUG org.springframework.test.context.support.TestPropertySourceUtils - Adding inlined properties to environment: {spring.jmx.enabled=false, org.springframework.boot.test.context.SpringBootTestContextBootstrapper=true}
 _ __  _ __ ___   __ _ _ __ __ _ _ __ ___  _ __ ___   ___ _ __
| '_ \| '__/ _ \ / _` | '__/ _` | '_ ` _ \| '_ ` _ \ / _ \ '__|
| |_) | | | (_) | (_| | | | (_| | | | | | | | | | | |  __/ |
| .__/|_|  \___/ \__, |_|  \__,_|_| |_| |_|_| |_| |_|\___|_|
|_|              |___/

 ______ _ _ __ ___   __ _ _ __    _ __   _____      __
|_  / _` | '_ ` _ \ / _` | '_ \  | '_ \ / _ \ \ /\ / /
 / / (_| | | | | | | (_| | | | | | | | | (_) \ V  V /
/___\__,_|_| |_| |_|\__,_|_| |_| |_| |_|\___/ \_/\_/
2023-01-28 13:57:12.620  INFO 2167 --- [           main] p.s.core.application.FooApplicationTest  : Starting FooApplicationTest using Java 11.0.17 on jenkinsagent1 with PID 2167 (started by reiya24 in /home/reiya24/jenkins_agent1/workspace/belajar pipeline)
2023-01-28 13:57:12.634  INFO 2167 --- [           main] p.s.core.application.FooApplicationTest  : No active profile set, falling back to default profiles: default
2023-01-28 13:57:14.368  INFO 2167 --- [           main] p.s.core.application.FooApplicationTest  : Started FooApplicationTest in 2.697 seconds (JVM running for 5.967)
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 4.701 s - in programmerzamannow.spring.core.application.FooApplicationTest
[INFO] Running programmerzamannow.spring.core.application.WithoutSpringBootTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.41 s - in programmerzamannow.spring.core.application.WithoutSpringBootTest
[INFO] Running programmerzamannow.spring.core.BeanNameTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.097 s - in programmerzamannow.spring.core.BeanNameTest
[INFO] Running programmerzamannow.spring.core.ImportTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.143 s - in programmerzamannow.spring.core.ImportTest
[INFO] Running programmerzamannow.spring.core.BeanFactoryTest
[programmerzamannow.spring.core.data.Foo@3c3a0032, programmerzamannow.spring.core.data.Foo@7ceb4478, programmerzamannow.spring.core.data.Foo@7fdab70c]
{foo=programmerzamannow.spring.core.data.Foo@3c3a0032, foo2=programmerzamannow.spring.core.data.Foo@7ceb4478, foo3=programmerzamannow.spring.core.data.Foo@7fdab70c}
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.105 s - in programmerzamannow.spring.core.BeanFactoryTest
[INFO] Running programmerzamannow.spring.core.InheritanceTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.051 s - in programmerzamannow.spring.core.InheritanceTest
[INFO] Running programmerzamannow.spring.core.FactoryTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.057 s - in programmerzamannow.spring.core.FactoryTest
[INFO] Running programmerzamannow.spring.core.BeanPostProcessorTest
2023-01-28 13:57:16.450  INFO 2167 --- [           main] p.s.c.p.IdGeneratorBeanPostProcessor     : Id Generator Processor for Bean beanPostProcessorTest.TestConfiguration
2023-01-28 13:57:16.457  INFO 2167 --- [           main] p.s.c.p.IdGeneratorBeanPostProcessor     : Id Generator Processor for Bean programmerzamannow.spring.core.data.Car
2023-01-28 13:57:16.458  INFO 2167 --- [           main] p.s.c.p.IdGeneratorBeanPostProcessor     : Set Id Generator for Bean programmerzamannow.spring.core.data.Car
c236fea5-6b11-4956-b66d-0b7daa2f15ae
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.06 s - in programmerzamannow.spring.core.BeanPostProcessorTest
[INFO] Running programmerzamannow.spring.core.BeanFactoryPostProcessorTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.041 s - in programmerzamannow.spring.core.BeanFactoryPostProcessorTest
[INFO] Running programmerzamannow.spring.core.AwareTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.033 s - in programmerzamannow.spring.core.AwareTest
[INFO] Running programmerzamannow.spring.core.ApplicationContextTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.023 s - in programmerzamannow.spring.core.ApplicationContextTest
[INFO] Running programmerzamannow.spring.core.DuplicateTest
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.08 s - in programmerzamannow.spring.core.DuplicateTest
[INFO] Running programmerzamannow.spring.core.OrderedTest
2023-01-28 13:57:16.721  INFO 2167 --- [           main] p.s.c.p.IdGeneratorBeanPostProcessor     : Id Generator Processor for Bean orderedTest.TestConfiguration
2023-01-28 13:57:16.722  INFO 2167 --- [           main] s.c.p.PrefixIdGeneratorBeanPostProcessor : Prefix Id Generator Processor for Bean orderedTest.TestConfiguration
2023-01-28 13:57:16.723  INFO 2167 --- [           main] p.s.c.p.IdGeneratorBeanPostProcessor     : Id Generator Processor for Bean programmerzamannow.spring.core.data.Car
2023-01-28 13:57:16.723  INFO 2167 --- [           main] p.s.c.p.IdGeneratorBeanPostProcessor     : Set Id Generator for Bean programmerzamannow.spring.core.data.Car
2023-01-28 13:57:16.723  INFO 2167 --- [           main] s.c.p.PrefixIdGeneratorBeanPostProcessor : Prefix Id Generator Processor for Bean programmerzamannow.spring.core.data.Car
2023-01-28 13:57:16.724  INFO 2167 --- [           main] s.c.p.PrefixIdGeneratorBeanPostProcessor : Prefix Set Id Generator for Bean programmerzamannow.spring.core.data.Car
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.055 s - in programmerzamannow.spring.core.OrderedTest
[INFO] Running programmerzamannow.spring.core.EventListenerTest
2023-01-28 13:57:16.808  INFO 2167 --- [           main] p.s.core.listener.LoginSuccessListener   : Success login for user User(username=eko)
2023-01-28 13:57:16.826  INFO 2167 --- [           main] p.s.c.l.LoginAgainSuccessListener        : Success login again for user User(username=eko)
2023-01-28 13:57:16.827  INFO 2167 --- [           main] p.spring.core.listener.UserListener      : Success login again for user User(username=eko)
2023-01-28 13:57:16.827  INFO 2167 --- [           main] p.spring.core.listener.UserListener      : Success login again for user User(username=eko)
2023-01-28 13:57:16.828  INFO 2167 --- [           main] p.spring.core.listener.UserListener      : Success login again for user User(username=eko)
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.083 s - in programmerzamannow.spring.core.EventListenerTest
[INFO] Running programmerzamannow.spring.core.ComponentTest
[INFO] Tests run: 5, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.631 s - in programmerzamannow.spring.core.ComponentTest
[INFO] Running programmerzamannow.spring.core.DependsOnTest
2023-01-28 13:57:17.524  INFO 2167 --- [           main] p.spring.core.DependsOnConfiguration     : Create new Bar
2023-01-28 13:57:17.532  INFO 2167 --- [           main] p.spring.core.DependsOnConfiguration     : Create new Foo
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.021 s - in programmerzamannow.spring.core.DependsOnTest
[INFO] Running programmerzamannow.spring.core.LifeCycleTest
2023-01-28 13:57:17.585  INFO 2167 --- [           main] p.spring.core.data.Connection            : Connection is ready to be used
2023-01-28 13:57:17.598  INFO 2167 --- [           main] p.spring.core.data.Server                : Start Server
2023-01-28 13:57:17.641  INFO 2167 --- [           main] p.spring.core.data.Connection            : Connection is ready to be used
2023-01-28 13:57:17.642  INFO 2167 --- [           main] p.spring.core.data.Server                : Start Server
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.097 s - in programmerzamannow.spring.core.LifeCycleTest
[INFO] Running programmerzamannow.spring.core.OptionalTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.053 s - in programmerzamannow.spring.core.OptionalTest
[INFO] Running programmerzamannow.spring.core.DependencyInjectionTest
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.072 s - in programmerzamannow.spring.core.DependencyInjectionTest
[INFO] Running programmerzamannow.spring.core.ScopeTest
2023-01-28 13:57:17.823  INFO 2167 --- [           main] o.s.c.a.ConfigurationClassEnhancer       : @Bean method ScopeConfiguration.customScopeConfigurer is non-static and returns an object assignable to Spring's BeanFactoryPostProcessor interface. This will result in a failure to process annotations such as @Autowired, @Resource and @PostConstruct within the method's declaring @Configuration class. Add the 'static' modifier to this method to avoid these container lifecycle issues; see @Bean javadoc for complete details.
2023-01-28 13:57:17.842  INFO 2167 --- [           main] p.spring.core.ScopeConfiguration         : Create new Foo
2023-01-28 13:57:17.849  INFO 2167 --- [           main] p.spring.core.ScopeConfiguration         : Create new Foo
2023-01-28 13:57:17.851  INFO 2167 --- [           main] p.spring.core.ScopeConfiguration         : Create new Foo
2023-01-28 13:57:17.869  INFO 2167 --- [           main] o.s.c.a.ConfigurationClassEnhancer       : @Bean method ScopeConfiguration.customScopeConfigurer is non-static and returns an object assignable to Spring's BeanFactoryPostProcessor interface. This will result in a failure to process annotations such as @Autowired, @Resource and @PostConstruct within the method's declaring @Configuration class. Add the 'static' modifier to this method to avoid these container lifecycle issues; see @Bean javadoc for complete details.
2023-01-28 13:57:17.881  INFO 2167 --- [           main] p.spring.core.ScopeConfiguration         : Create new Bar
2023-01-28 13:57:17.883  INFO 2167 --- [           main] p.spring.core.ScopeConfiguration         : Create new Bar
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.072 s - in programmerzamannow.spring.core.ScopeTest
[INFO] Running programmerzamannow.spring.core.CyclicTest
2023-01-28 13:57:17.924  WARN 2167 --- [           main] s.c.a.AnnotationConfigApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'cyclicA' defined in programmerzamannow.spring.core.CyclicConfiguration: Unsatisfied dependency expressed through method 'cyclicA' parameter 0; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'cyclicB' defined in programmerzamannow.spring.core.CyclicConfiguration: Unsatisfied dependency expressed through method 'cyclicB' parameter 0; nested exception is org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'cyclicC' defined in programmerzamannow.spring.core.CyclicConfiguration: Unsatisfied dependency expressed through method 'cyclicC' parameter 0; nested exception is org.springframework.beans.factory.BeanCurrentlyInCreationException: Error creating bean with name 'cyclicA': Requested bean is currently in creation: Is there an unresolvable circular reference?
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.046 s - in programmerzamannow.spring.core.CyclicTest
[INFO] Running programmerzamannow.spring.core.PrimaryTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.047 s - in programmerzamannow.spring.core.PrimaryTest
[INFO] Running programmerzamannow.spring.core.BeanTest
2023-01-28 13:57:18.020  INFO 2167 --- [           main] p.spring.core.BeanConfiguration          : Create new foo
2023-01-28 13:57:18.041  INFO 2167 --- [           main] p.spring.core.BeanConfiguration          : Create new foo
[INFO] Tests run: 2, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.056 s - in programmerzamannow.spring.core.BeanTest
[INFO] Running programmerzamannow.spring.core.ScanTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.049 s - in programmerzamannow.spring.core.ScanTest
[INFO] Running programmerzamannow.spring.core.DatabaseTest
[INFO] Tests run: 1, Failures: 0, Errors: 0, Skipped: 0, Time elapsed: 0.007 s - in programmerzamannow.spring.core.DatabaseTest
[INFO] 
[INFO] Results:
[INFO] 
[INFO] Tests run: 34, Failures: 0, Errors: 0, Skipped: 0
[INFO] 
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  16.051 s
[INFO] Finished at: 2023-01-28T13:57:18Z
[INFO] ------------------------------------------------------------------------
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```