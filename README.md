## 🚀 Como Executar a Aplicação

Siga o passo a passo abaixo para rodar o projeto corretamente em sua máquina.

---

### 📦 1. Pré-requisitos

Antes de começar, certifique-se de ter instalado:

* Java (versão 17 ou superior)
* Maven
* Docker Desktop

---

### 🐳 2. Subindo o Banco de Dados com Docker

1. Inicie o Docker Desktop
2. No terminal, execute o comando abaixo para subir o banco (exemplo com MySQL):

```bash
docker run -d \
  --name mysql-container \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=meubanco \
  -e MYSQL_USER=usuario \
  -e MYSQL_PASSWORD=senha \
  -p 3306:3306 \
  mysql:8
```

3. Verifique se o container está rodando:

```bash
docker ps
```

---

### ⚙️ 3. Configuração da Aplicação

Abra o arquivo:

```
src/main/resources/application.properties
```

Configure as propriedades de conexão com o banco:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/meubanco
spring.datasource.username=usuario
spring.datasource.password=senha

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

server.port=8080
```

#### 🔧 Ajustes importantes:

* **Porta do banco:** 3306 (ou a que você configurou no Docker)
* **Usuário e senha:** devem ser iguais aos definidos no container
* **Porta da aplicação:** pode ser alterada em `server.port`

---

### ▶️ 4. Executando a Aplicação

No diretório raiz do projeto (onde está o `pom.xml`), execute:

```bash
mvn spring-boot:run
```

Se tudo estiver correto, a aplicação será iniciada e ficará disponível em:

```
http://localhost:8080
```

---

### 🧪 5. Testando a API

Você pode testar os endpoints utilizando:

* Postman
* Insomnia
* Navegador (para requisições GET)

---

### 🛑 6. Parando os Serviços

Para parar o container do banco:

```bash
docker stop mysql-container
```

Para remover o container:

```bash
docker rm mysql-container
```

---

### ⚠️ Possíveis Problemas

* **Erro de porta em uso:** altere a porta no `application.properties` ou no Docker
* **Erro de conexão com banco:** verifique se o container está rodando e as credenciais estão corretas
* **Erro no Maven:** verifique se o Maven está instalado e configurado no PATH

---

### ✅ Pronto!

Agora sua aplicação deve estar rodando corretamente 🚀
