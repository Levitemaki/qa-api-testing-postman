# ⚙️ Portfólio de Testes de API (Back-end)

Este documento contém os cenários de testes manuais de API realizados utilizando o **Postman**. O objetivo é demonstrar a capacidade de interagir com serviços Back-end, validando os verbos HTTP (GET e POST), o envio de *payloads* em JSON e o tratamento correto dos Status Codes.

**Ferramenta utilizada:** Postman  
**API Alvo (Ambiente de Teste):** `https://jsonplaceholder.typicode.com`

---

## 🟢 Teste 01: [GET] Busca de Usuário Específico (Caminho Feliz)
* **Objetivo:** Validar se a API retorna corretamente os dados de um usuário existente.
* **Método:** `GET`
* **Endpoint (URL):** `/users/1`
* **Resultado Esperado:** A API deve retornar o Status Code `200 OK` e um corpo (body) em formato JSON contendo os dados do usuário correspondente ao ID 1.
* **Resultado Atual:** Status Code `200 OK` recebido com sucesso. O JSON retornou os dados corretamente. **[Passou ✅]**

---

## 🔵 Teste 02: [POST] Criação de Novo Usuário (Caminho Feliz)
* **Objetivo:** Validar se a API permite a criação de um novo registro de usuário através do envio de um *payload* (corpo da requisição) em formato JSON.
* **Método:** `POST`
* **Endpoint (URL):** `/users`
* **Corpo (Body) Enviado:**
  ```json
  {
    "name": "Levitemaki",
    "username": "qa_tester",
    "email": "teste@qa.com"
  }
  ```
* **Resultado Esperado:** A API deve aceitar o pacote de dados e retornar o Status Code `201 Created`, confirmando o registro no banco de dados.
* **Resultado Atual:** Status Code `201 Created` recebido com sucesso. **[Passou ✅]**

---

## 🔴 Teste 03: [GET] Busca de Usuário Inexistente (Teste Negativo)
* **Objetivo:** Validar o comportamento e o tratamento de erro da aplicação ao tentar buscar um ID de usuário que não existe no banco de dados.
* **Método:** `GET`
* **Endpoint (URL):** `/users/9999`
* **Resultado Esperado:** A aplicação não deve apresentar falha crítica de servidor (Status 500). Ela deve tratar a exceção e retornar o Status Code `404 Not Found`, indicando que o recurso não foi encontrado.
* **Resultado Atual:** Status Code `404 Not Found` recebido com sucesso. O sistema lidou com o teste negativo de forma elegante. **[Passou ✅]**
