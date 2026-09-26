# 🚀 KanbanFlow - Sistema Kanban com Autenticação JWT e Persistência JSON

O **KanbanFlow** é uma aplicação completa de gerenciamento visual de tarefas e projetos com **Autenticação JWT segura**, isolamento de dados por usuário, revogação de tokens (blacklist), dashboard analítico em tempo real e persistência puramente em arquivos JSON (sem banco de dados).

---

## 🛠️ Stack Tecnológica

- **Front-End**: Vanilla JavaScript (HTML5 / CSS3 / ES6+) com manipuladores de eventos assíncronos, formulários responsivos e suporte a temas (Modo Claro e Modo Escuro).
- **Back-End**: Servidor HTTP em Node.js com módulos nativos (`http`, `fs`, `path`, `crypto`).
- **Autenticação**: JSON Web Token (JWT) nativo HMAC-SHA256 contendo `jti` (UUID único do token) e expiração configurável.
- **Segurança de Senhas**: Criptografia unilateral segura via `crypto.scryptSync` com sal único por usuário.
- **Persistência**: Arquivos JSON locais (`kanban_data.json`, `users.json`, `revoked-tokens.json`).

---

## ⚙️ Variáveis de Ambiente

As seguintes variáveis de ambiente podem ser configuradas antes de iniciar o servidor (ou serão aplicados os valores padrão):

| Variável | Descrição | Valor Padrão |
| :--- | :--- | :--- |
| `PORT` | Porta de execução do servidor HTTP | `8080` |
| `JWT_SECRET` | Chave secreta usada para assinar e validar os tokens JWT | `kanbanflow_secret_key_jwt_2026` |
| `JWT_EXPIRATION` | Tempo de expiração do token JWT em segundos | `3600` (1 hora) |

---

## 📁 Estrutura de Diretórios Organizada

```
Kanban/
├── data/                       # 🗄️ Persistência dos bancos de dados JSON locais
│   ├── kanban_data.json        # Armazena quadros, colunas e tarefas dos usuários
│   ├── users.json              # Usuários e credenciais com hash seguro
│   └── revoked-tokens.json     # Blacklist de tokens JWT revogados
│
├── public/                     # 🌐 Recursos estáticos complementares (CSS, JS, Assets)
│   ├── css/
│   │   └── styles.css          # Design system, temas Claro/Escuro e layout responsivo
│   ├── js/
│   │   └── app.js              # Lógica de aplicação, drag-and-drop e auth JWT
│   └── assets/
│       └── favcon.png          # Favicon da aplicação
│
├── assets/                     # 🖼️ Ícones e recursos visuais locais
│   └── favcon.png
│
├── scripts/                    # 🛠️ Scripts utilitários de manutenção
│   └── migrate.js              # Script de migração de tarefas para usuários padrão
│
├── index.html                  # 🌐 Interface do usuário (na raiz do projeto)
├── server.js                   # 🚀 Servidor HTTP e endpoints de autenticação e API
└── README.md                   # 📖 Documentação do projeto
```

---

## 🚀 Como Iniciar a Aplicação

1. Entre na pasta do projeto (ou execute diretamente da raiz):
   ```cmd
   cd Kanban
   ```

2. (Opcional) Execute o script de migração:
   ```cmd
   node scripts/migrate.js
   ```

3. Inicie o servidor Node.js:
   ```cmd
   node server.js
   ```

4. Acesse no seu navegador: **[http://localhost:8080](http://localhost:8080)**
