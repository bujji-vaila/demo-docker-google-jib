Spring Boot app with Docker- Google jib

note: no need docker installed in your machine, need dockerhub account

step1 : write sping boot app using spring initializer(dependency modules, Spring web)

Step 2:Add one endpoint

        @RestController
		@RequestMapping("/")
		@SpringBootApplication
		public class DemoDocker1Application {

			public static void main(String[] args) {
				SpringApplication.run(DemoDocker1Application.class, args);
			}
			
			@GetMapping
			public String greetings() {
				return "hello welcome to docker demo";
			}

		}
   
Step 3: add google jib library in pom.xml file
           <plugin>
				<groupId>com.google.cloud.tools</groupId>
				<artifactId>jib-maven-plugin</artifactId>
				<version>3.3.2</version>
				<configuration>
					<to>
						<image>registry.hub.docker.com/<<dockerhub-username>>/demo-docker-google-jib</image>
					</to>
				</configuration>
			</plugin> 

		
Step 4. build the docker image
 
       mvn clean compile jib:build
        

Step 5. run the container by below command
   
   docker run --p 8080:8080 <<dockerloginid>>/demo-docker-google-jib
   
Step 6:  hit the browser url http://localhost:8080   

