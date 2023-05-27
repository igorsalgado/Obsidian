---
Data: 2023-05-22
Hora: 23:04
---
``Tags:`` #Java #Backend #POO #CleanArch 

---

## Resume

1.  Princípio da Responsabilidade Única (Single Responsibility Principle): Uma classe deve ter apenas uma única responsabilidade. Isso significa que uma classe deve ter apenas um motivo para mudar. Um exemplo em Java é a classe `Cliente` que tem a responsabilidade de representar um cliente e enviar e-mails relacionados a esse cliente.
<br>
    
2.  Princípio Aberto/Fechado (Open/Closed Principle): As entidades de software devem estar abertas para extensão, mas fechadas para modificação. Isso significa que você deve poder estender o comportamento de uma entidade sem precisar modificar seu código fonte. Um exemplo em Java é a classe abstrata `Forma`, que define o contrato do método `calcularArea()`, permitindo que classes como `Retangulo` e `Circulo` estendam esse comportamento sem modificar a classe `Forma`.
   <br>
    
3.  Princípio da Substituição de Liskov (Liskov Substitution Principle): Um objeto de uma classe derivada deve poder ser substituído por um objeto de sua classe base sem quebrar a funcionalidade do programa. Isso significa que a classe derivada deve ser compatível com a classe base em termos de comportamento e contrato. Um exemplo em Java é a hierarquia de classes `Animal`, onde as classes derivadas `Cachorro` e `Gato` podem ser substituídas pela classe base `Animal` sem causar problemas de funcionalidade.
   <br>
    
4.  Princípio da Inversão de Dependência (Dependency Inversion Principle): Estabelece que os módulos de alto nível não devem depender diretamente dos módulos de baixo nível. Em vez disso, ambos devem depender de abstrações. Isso significa que devemos depender de interfaces ou classes abstratas em vez de classes concretas. 
   Ao aplicar esse princípio, conseguimos escrever código mais flexível e extensível. Podemos facilmente substituir as implementações concretas por outras sem afetar o restante do sistema. Isso promove a reutilização de código e reduz o acoplamento entre os componentes do sistema.
   <br>
       
5.  Princípio da Segregação de Interface (Interface Segregation Principle): Enfatiza que os clientes não devem ser forçados a depender de interfaces que não utilizam. Em vez disso, as interfaces devem ser segregadas de acordo com as necessidades específicas dos clientes. 
   Ao seguir esse princípio, evitamos a criação de interfaces muito genéricas e coletivas, que podem levar a dependências desnecessárias e acoplamento indesejado. Em vez disso, dividimos as interfaces em unidades mais coesas e específicas, permitindo que os clientes dependam apenas das partes relevantes. 
   Ao aplicar o Princípio da Segregação de Interface, obtemos um sistema mais modular e flexível, facilitando a manutenção, evolução e reutilização de componentes.


## Content

#### S - Princípio da Responsabilidade Única

O Princípio da Responsabilidade Única afirma que uma classe deve ter apenas uma única responsabilidade. Em outras palavras, uma classe deve ter apenas um motivo para mudar. Isso ajuda a manter o código mais coeso e facilita a compreensão e a manutenção do mesmo.

```java
public class Cliente{ 
	private String nome;
	private String email;

public Cliente(String nome, String email) {
	this.nome = nome;
	this.email = email; 
} 

	public void enviarEmail(String mensagem) {
// Lógica para enviar o e-mail 
	} 
}
```

Neste exemplo, a classe `Cliente` tem a responsabilidade de representar um cliente e também de enviar e-mails relacionados a esse cliente. Essas duas responsabilidades são mantidas separadas, seguindo o princípio da responsabilidade única.

#### O - Princípio Aberto/Fechado

O Princípio Aberto/Fechado afirma que as entidades de software devem estar abertas para extensão, mas fechadas para modificação. Isso significa que você deve poder estender o comportamento de uma entidade sem precisar modificar seu código fonte. Isso promove a reutilização de código e reduz o impacto de alterações em outras partes do sistema.

```java
public abstract class Forma {
	public abstract double calcularArea();
}

public class Retangulo extends Forma {
	private double largura;
	private double altura;

	public Retangulo(double largura, double altura) {
		this.largula = largura;
		this.altura = altura;
	}

	@Override
	public double calcularArea() {
	return largula * altura
	}
}

public class Circulo extends Forma {
	private double raio;

	public Circulo(double raio) {
		this.raio = raio;
	}

	@Override
	public double CalcularArea() {
		return Math.PI * raio * raio;
	}	
}
```

Neste exemplo, a classe abstrata `Forma` define um contrato com o método `calcularArea()`, permitindo que outras classes, como `Retangulo` e `Circulo`, estendam esse comportamento sem modificar o código da classe `Forma`. Isso nos permite adicionar facilmente novas formas geométricas sem alterar o código existente.

## L - Princípio da Substituição de Liskov (Liskov Substitution Principle)

O Princípio da Substituição de Liskov afirma que um objeto de uma classe derivada deve poder ser substituído por um objeto de sua classe base sem quebrar a funcionalidade do programa. Isso significa que a classe derivada deve ser compatível com a classe base em termos de comportamento e contrato.

```java
public abstract class Animal {
    public abstract void fazerBarulho();
}

public class Cachorro extends Animal {
    @Override
    public void fazerBarulho() {
        System.out.println("Au Au!");
    }
}

public class Gato extends Animal {
    @Override
    public void fazerBarulho() {
        System.out.println("Miau!");
    }
}
```

Neste exemplo, a classe abstrata `Animal` define um contrato com o método `fazerBarulho()`. As classes derivadas `Cachorro` e `Gato` implementam esse método de acordo com o comportamento esperado para cada animal. Podemos tratar objetos do tipo `Cachorro` e `Gato` de forma polimórfica como objetos do tipo `Animal`, garantindo a substituição de Liskov.

## I - Princípio da Inversão de Dependência (Dependency Inversion Principle)

O Princípio da Inversão de Dependência afirma que os módulos de alto nível não devem depender diretamente dos módulos de baixo nível. Ambos devem depender de abstrações. Além disso, abstrações não devem depender de detalhes, mas detalhes devem depender de abstrações.

Em termos práticos, isso significa que devemos depender de interfaces ou classes abstratas em vez de classes concretas. Isso nos permite escrever código mais flexível e extensível, pois podemos substituir facilmente as implementações concretas por outras sem afetar o restante do sistema.

```java
public interface EmailSender {
    void sendEmail(String to, String subject, String content);
}

public class SmtpEmailSender implements EmailSender {
    public void sendEmail(String to, String subject, String content) {
        // Lógica para enviar e-mail via SMTP
    }
}

public class SendGridEmailSender implements EmailSender {
    public void sendEmail(String to, String subject, String content) {
        // Lógica para enviar e-mail via SendGrid
    }
}

public class Cliente {
    private EmailSender emailSender;

    public Cliente(EmailSender emailSender) {
        this.emailSender = emailSender;
    }

    public void enviarEmail(String to, String subject, String content) {
        emailSender.sendEmail(to, subject, content);
    }
}

```

Neste exemplo, o princípio da inversão de dependência é aplicado ao utilizar a interface `EmailSender` como dependência na classe `Cliente`. Isso permite que diferentes implementações de `EmailSender`, como `SmtpEmailSender` e `SendGridEmailSender`, sejam injetadas no `Cliente` sem que ele precise saber dos detalhes de implementação.

## D - Princípio da Segregação de Interface (Interface Segregation Principle)

O Princípio da Segregação de Interface afirma que os clientes não devem ser forçados a depender de interfaces que não utilizam. Em vez disso, as interfaces devem ser segregadas de acordo com as necessidades específicas dos clientes.

Esse princípio promove a coesão e evita a dependência desnecessária de funcionalidades não utilizadas. Em outras palavras, é preferível ter várias interfaces específicas em vez de uma única interface geral.

```java
public interface EmailSender {
    void sendEmail(String to, String subject, String content);
}

public interface EmailTemplateGenerator {
    String generateTemplate(String templateName);
}

public class SmtpEmailSender implements EmailSender, EmailTemplateGenerator {
    public void sendEmail(String to, String subject, String content) {
        // Lógica para enviar e-mail via SMTP
    }

    public String generateTemplate(String templateName) {
        // Lógica para gerar template de e-mail
    }
}

public class SendGridEmailSender implements EmailSender {
    public void sendEmail(String to, String subject, String content) {
        // Lógica para enviar e-mail via SendGrid
    }
}

public class Cliente {
    private EmailSender emailSender;

    public Cliente(EmailSender emailSender) {
        this.emailSender = emailSender;
    }

    public void enviarEmail(String to, String subject, String content) {
        emailSender.sendEmail(to, subject, content);
    }
}

```

Neste exemplo, as interfaces `EmailSender` e `EmailTemplateGenerator` são segregadas de acordo com suas funcionalidades específicas. Dessa forma, os clientes podem depender apenas das interfaces relevantes para suas necessidades, evitando a dependência de recursos não utilizados.


## Conclusão

Esses princípios SOLID fornecem diretrizes valiosas para escrever código de qualidade, flexível e de fácil manutenção. Ao aplicar esses princípios em seus projetos Java, você pode criar um software mais robusto e escalável.

## Referências
-  [SOLID: The First 5 Principles of Object-Oriented Design](https://scotch.io/bar-talk/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)

