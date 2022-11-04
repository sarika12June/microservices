#Spring interview Question
----------------------------------------------------
Annotations
----------------------------------------------------
@Autowired --> DI
@Qualifier --> Ambiguity => no dynamic parameter use @resource 
@Resource  --> DI + Ambiguity 

what is spring use of context dependence  ?
add the context name space in application-context.xml so that we can enable component scan

<context:component-scan base-package ="rootPkg"></context:component-scan>

payment => paytm ,phonephe => now use @Qualifier('paytm')

Resource=>application.properties{beanName:'paytm'} =>beanName=phonepe => load property file 
@propertySource(value={"classpath :application.properties"})
@Resource('${beanName}')


Spring Boot cheat sheet Annotations
----------------------------------------------------
@SpringBootApplication =>
	 @EnableAutoConfiguration => based on dependence it configure the bean in the project
	 @ComponentScan  =>scan the bean to visbile to IOC
	 @Configuration  =>define the bean defination
	 
@Sterotype Annotations:manage the life cycle by spring
  @Component(parent),@service,@RestController/Controller and @Repositry
  
Spring Core related Annotations:
----------------------------------------------------
@Configuration : we can define on classes , if we do not use spring bean life cycle either xml or annotation ,used by IOC as source bean defination
@Bean : we can define in configuration class , later inject bean and use it
@Autowired  :DI
@Qualifier : Ambiguity => no dynamic parameter use @resource 
@Primary :on the class level define @primary , give priority for specfic bean like phonephe =>mutiple data source
@Lazy  :by default spring bean eager loading ,if u want tell IOC do not create  bean untill i ask using @Autowired 
@Value  :load the meta data from property file using @value('${mail.from}')
@PropertySource :Load the custom application property, spring automatically load  application property
@ConfigurationProperties :if u bunch of key and value in properties file and bind to single bean class @ConfigurationProperties(@prefix:'mail')
@Profile:dev,stage to switch from one env to another,like application_dev.properties ,application_stage.properties ,define active profile in application  properties
@Scope: singleton :single object for context
        prototype: create bean instance based on number of hits to API
		we can use below scope only in Spring ApplicationContext (Web aware applications)
		Request :on every http request
		Session : from  same window same instance  will serverd , if you use  different instance get created
		
		


REST API related Annotations:
------------------------------------------------
@RestController   :class expose the API using http methods
@RequestMapping   :define the http  like post,get
@GetMapping    	  :specfic role to get http methods
@PostMapping   	  :specfic role to post http methods
@PutMapping    	  :specfic role to put http methods
@DeleteMapping 	  :specfic role to delete http methods
@RequestBody      :used in post method , save pojo to db,deserlize the pojo
@PathVariable     :it retives query string from uri. get specific studentid =>not input404
@RequestParam     : from query string using name => not exception
@RestControllerAdvice @ExceptionHandler :used to handle exceptions in the code



Spring Data JPA related annotations:
------------------------------------------------------------
@Entity    :telling to JPA and hiberate this is object to peform the DB operation
@Table     :to create table based on given text
@Column    :define column name based on given text
@Transactional  : if some wrong happens asscoiation mapping has be rollbacked with islation and progagation 
Entity class relationships 
@OnetoOne :Student with address 
@OnetoMany  :one emp can apply for mutiple phone numbers with: Target Enitity fetch type and define joinColumn
@ManytoOne  :many course can appplied by one student in course class define student Entity :Target Enitity fetch type and define joinColumn
@ManytoMany :



Security related annotations:
------------------------------------------------------------
@crossOrigin 
@Secured
@preAuthorize
@PermitAll

Cache  related annotations:
------------------------------------------------------------
@EnableCaching
@Cacheable
@CachePut
@CacheEvict


AOP  related annotations:
------------------------------------------------------------
@Aspect
@PointCut
@AfterRunning
@AfterThowing
@Around
@Before
  
  
  
  


