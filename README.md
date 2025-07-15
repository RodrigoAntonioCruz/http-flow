
# 🚀 O que acontece quando digito http://www.netshoes.com.br no navegador?

Este documento explica passo a passo o que ocorre entre o cliente (browser) e o servidor quando digitamos uma URL como:

```
http://www.netshoes.com.br
```

---

## ✅ Passo a Passo

### 1. Digitação da URL e Parsing no Browser

- O usuário digita a URL e pressiona Enter.
- O navegador faz o parsing, dividindo:
  - Protocolo → `http`
  - Host → `www.netshoes.com.br`
  - Porta → 80 (padrão HTTP)
  - Caminho → `/`

---

### 2. Verificação do Cache Local

- O browser verifica se há:
  - Resposta HTTP salva em cache (HTML, CSS, JS).
  - IP do domínio salvo no cache DNS.
- Se existir cache válido, pode evitar novas requisições.

---

### 3. Resolução de Nome (DNS Lookup)

- Se não está em cache:
  - O navegador consulta o servidor DNS para descobrir o IP do domínio.
- Exemplo de resposta DNS:
  ```
  www.netshoes.com.br → 186.202.153.41
  ```

---

### 4. Estabelecimento de Conexão TCP

- Com o IP em mãos, o browser estabelece conexão TCP:
  - Porta de destino: 80
- Handshake em 3 etapas:
  - SYN → cliente → servidor
  - SYN-ACK ← servidor ← cliente
  - ACK → cliente → servidor

---

### 5. Envio da Requisição HTTP

- O navegador envia uma requisição HTTP ao servidor:

**Exemplo de requisição:**
```
GET / HTTP/1.1
Host: www.netshoes.com.br
User-Agent: Mozilla/5.0
Accept: text/html
```

---

### 6. Processamento da Requisição no Servidor

- O servidor:
  - Autentica se necessário.
  - Executa lógica de negócio.
  - Busca dados ou arquivos no disco/banco de dados.

---

### 7. Envio da Resposta HTTP

- O servidor monta a resposta HTTP:

**Exemplo de resposta:**
```
HTTP/1.1 200 OK
Content-Type: text/html; charset=UTF-8
Content-Length: 2456

<!DOCTYPE html>
<html>
  <head>...</head>
  <body>...</body>
</html>
```

---

### 8. Renderização no Browser

- O navegador:
  - Interpreta o HTML.
  - Faz novas requisições (CSS, JS, imagens).
  - Renderiza a página para o usuário.

---

### 9. Encerramento da Conexão TCP

- Dependendo do header `Connection`:
  - Pode encerrar ou manter a conexão aberta para futuras requisições.

---

## ✅ Diagrama Simplificado

```plaintext
┌────────────┐
│  Browser   │
└─────┬──────┘
      │
      │ Digita URL
      ▼
┌──────────────┐
│   Cache      │
└─────┬────────┘
      │
      ▼
┌──────────────┐
│ DNS Lookup   │
└─────┬────────┘
      │
      ▼
┌──────────────┐
│ TCP Handshake│
└─────┬────────┘
      │
      ▼
┌──────────────┐
│ HTTP Request │
│  (GET /)     │
└─────┬────────┘
      │
      ▼
┌──────────────┐
│   Servidor   │
└─────┬────────┘
      │
      ▼
┌──────────────┐
│ HTTP Response│
│ (HTML, etc.) │
└─────┬────────┘
      │
      ▼
┌────────────┐
│  Browser   │
└────────────┘
      │
      ▼
Renderização da página
```

---

## ✅ Resumo Final

- O browser interpreta a URL.
- Resolve o domínio via DNS.
- Cria conexão TCP.
- Envia requisição HTTP.
- O servidor responde.
- O navegador renderiza a página.

Tudo isso acontece em **milissegundos**!

---
