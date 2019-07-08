## Lombok is a tool
https://projectlombok.org

#### Annotation for Lombok
import lombok.Data //<--- This is taken

@Data   <---- this gives us getters and setters
@AllArgsConstructor  <----- this gives us a constructor

public class Address() {
  private String streetName;
  private String city;
  private String State;
  private String Zip;
}

<dependencies>
  <dependency>
    <groupId>org.projectlombok</groupId>
    <artifact>
