# Taller03-SOLID

## Error clase AppWeb.java

/*

public class AppWeb {
    LogIn logIn;
    LogInAdmin logInAdmin;
    MySQL mySQL;
    public AppWeb (LogIn logIn, MySQL mySQL) {
        // Logic
    }
    public AppWeb (LogInAdmin logInAdmin, MySQL mySQL) {
        // Logic
    }
    public void connectToDatabase (MySQL mySQL) {
        // Logic
    }
}
*\

Principio Dependency Inversion Principle
Este depende de algo en contreto, el cual seria MYsql

## Solucion
Transformar MYSQL a una interfaz para que este no dependa de la clase en concreto

public interface MySQL {
    void insert(String statement);
    void select(String statement);
    void delete(String statement);
    void update(String statement);
}