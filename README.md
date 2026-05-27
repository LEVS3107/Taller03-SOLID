# Taller03-SOLID

## Error clase LogIn
La clase LogIn posee muchas responsabilidades, viola el principio de Single Responsability Principle, también el de Dependency Inversion Principle.

La clase tiene mas de una responsabilidad:
- Realiza el proceso de login
- Muestra mensajes
- Guarda usuarios en la base de datos

Y el principio de SRP dice que una clase debe cumplir una unica responsabilidad.

Por otro lado tambien viola el principio DIP, el principio DIP dice que seria mejor trabajar con abstracciones, (clases abstractas o interfaces) ya que la logica se encuentra dentro de la misma clase.

Para arreglar estos dos principios hay que separar la logica que se encuentra dentro de su clase tambien, para ello se separa con una interfaz llamada UserRepository, para que la clase LogIn solo maneje la autenticación.

    public class LogIn {
        public void log (User user) {
            System.out.println("Has access to the website");
            insertUserInDatabase(user);
            // Logic
        }
        public void insertUserInDatabase(User user){
            // Insert user in database
        }
    }
Creamos la interfaz UserRepository
    
    public interface UserRepository{
        void save(User user);
    }

    public class MySQLUserRepository implements UserRepository{
        @Override

        public void save (User user){
            System.out.println("Insert user into SQL");
        }
    }

Entonces ya cuando la logica sale fuera de la clase, la clase LogIn quedaria asi:

    public class LogIn {

        private UserRepository repository;

        public LogIn(UserRepository repository) {
            this.repository = repository;
        }

        public void log(User user) {

            System.out.println("Has access to the website");

            repository.save(user);
        }
    }
    