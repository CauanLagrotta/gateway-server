# Gateway Server

API Gateway do projeto Saloon Platform.

## Visão Geral

O Gateway Server é o ponto de entrada único para todas as requisições da plataforma. Ele roteia as chamadas para os microsserviços apropriados, exige autenticação via OAuth2 e realiza balanceamento de carga.

## Porta

**5000**

## Funcionalidades

- Roteamento de requisições para microsserviços
- Autenticação e autorização via OAuth2 Resource Server
- Balanceamento de carga com Spring Cloud LoadBalancer
- Descoberta de serviços via Eureka
- Proxy reverso para todos os serviços

## Endpoints

| Método | Caminho | Descrição |
|--------|---------|-----------|
| * | `/user/**` | Roteia para user-service |
| * | `/saloon/**` | Roteia para saloon-service |
| * | `/category/**` | Roteia para category-service |
| * | `/service-offering/**` | Roteia para service-offering |
| * | `/booking/**` | Roteia para booking-service |
| * | `/payment/**` | Roteia para payment-service |
| * | `/notification/**` | Roteia para notifications |
| * | `/review/**` | Roteia para review |

## Tecnologias

- Spring Boot 4.1.0
- Spring Cloud Gateway Server WebFlux
- Spring Security OAuth2 Resource Server
- Spring Cloud LoadBalancer
- Java 21

## Como Rodar

```bash
mvn clean package
java -jar target/gateway-server-0.0.1-SNAPSHOT.jar
```

## Configuração

As rotas são configuradas via `application.yml` e descobertas dinamicamente via Eureka. O serviço utiliza Netty (WebFlux) para alta performance.

## Segurança

- Exige token OAuth2 válido para todas as requisições
- Valida tokens via-configuração do resource server
