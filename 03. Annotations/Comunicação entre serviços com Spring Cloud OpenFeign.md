---
Data: 2023-05-28
Hora: 16:20
---
``Tags:`` #Microservices #SpringCloud

---

## Resumo

Spring Cloud OpenFeign é uma biblioteca poderosa que simplifica a comunicação entre serviços em um ambiente de microsserviços baseado em Spring. Ele permite que você defina interfaces de cliente declarativas, eliminando a necessidade de escrever código manualmente para lidar com a comunicação HTTP. Isso torna o desenvolvimento de microsserviços mais eficiente e produtivo, permitindo que você se concentre nas funcionalidades do seu serviço em vez de se preocupar com a comunicação entre eles.

## Conteúdo

##### Utilizando o Spring Cloud OpenFeign

Para utilizarmos o Spring Cloud OpenFeign precisamos adicionar sua dependência no projeto.

```xml
<dependency>
	<groupId>org.springframework.cloud</groupId>
	<artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>
```

Precisamos também habilitar o feign numa classe de configuração do Spring, nesse exemplo iremos utilizar a classe “Application”, para isso vamos adicionar a anotação @EnableFeignClients

```java 
@EnableFeignClients
@SpringBootApplication
public class HrPayrollApplication {
	public static void main(String[] args) {
	SpringApplication.run(HrPayrollApplication.class, args);
	}
}
```

Com isso, já podemos utilizar os recursos do OpenFeign em nossa aplicação,.

#### Integração com o Ribbon

[[Ribbon]], também faz parte do conjunto de biblioteca criadas pela Netflix, e trata-se de um conceito de Client Side Load Balance que por sua vez integra-se com o [[Service Discovery Eureka]].


## Conclusões

O Spring Cloud OpenFeign é uma ótima opção para criação de clientes de serviços, ele disponibiliza de forma clara e prática de nos comunicarmos com outros Web Services e embora ele possua um alto nível de abstração, e também disponibiliza uma ampla parametrização e possibilidade de encaixar classes de configuração personalizadas.

## Referências

- [[Fundamentos dos Microservices]]
