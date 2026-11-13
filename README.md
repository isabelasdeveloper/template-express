# 🚀 Template de API utilizando Node.js

Este repositório é um template inicial: a estrutura básica da API já está pronta para receber as rotas e as regras de negócio.

## 🛠️ Tecnologias

| Tecnologia | Versão | Para que serve |
|---|---|---|
| [Node.js](https://nodejs.org/) | 18 ou superior | Ambiente que executa o JavaScript no servidor. |
| [Express](https://expressjs.com/) | 5.3.0 | Framework que cria o servidor, as rotas e os middlewares da API. |
| [TypeScript](https://www.typescriptlang.org/) | 7.0.2 | Adiciona tipagem ao JavaScript e ajuda a encontrar erros antes de rodar o código. |
| [Zod](https://zod.dev/) | 4.6.7 | Valida os dados que chegam nas requisições (body, params, query). |
| [tsx](https://tsx.is/) | 4.23.15 | Roda arquivos TypeScript direto, sem compilar, e reinicia o servidor a cada alteração. |
| @types/express | 5.0.6 | Tipos do Express para o TypeScript. |
| @types/node | 26.6.6 | Tipos do Node.js para o TypeScript. |

---

## 📁 Estrutura de pastas

```
rocketlog/
├── src/
│   ├── middlewares/
│   │   └── error-handler.ts   # Trata todos os erros da API em um só lugar
│   ├── utils/
│   │   └── AppError.ts        # Classe para criar erros personalizados
│   ├── app.ts                 # Configura o Express (JSON, rotas, middlewares)
│   └── server.ts              # Inicia o servidor na porta 3333
├── package.json               # Dependências e scripts do projeto
└── tsconfig.json              # Configurações do TypeScript
```

### O que cada arquivo faz

- **`server.ts`** — Ponto de entrada da aplicação. Importa o `app` e coloca o servidor para rodar na porta **3333**.
- **`app.ts`** — Cria a aplicação Express, habilita o recebimento de JSON (`express.json()`) e registra o middleware de erros. É aqui que as rotas serão adicionadas.
- **`utils/AppError.ts`** — Classe usada para lançar erros conhecidos, com mensagem e código de status HTTP (o padrão é `400`).
  ```ts
  throw new AppError("Entrega não encontrada", 404);
  ```
- **`middlewares/error-handler.ts`** — Captura qualquer erro lançado na API e devolve uma resposta padronizada:
  - `AppError` → status definido no erro + mensagem
  - `ZodError` (dados inválidos) → status `400` + detalhes da validação
  - Qualquer outro erro → status `500`

---

## ⚙️ Configurações do TypeScript

Alguns pontos importantes do `tsconfig.json`:

- **`paths` (`@/*`)** — Atalho para importar arquivos da pasta `src`. Em vez de `../../utils/AppError`, use `@/utils/AppError`.
- **`strict`** — Ativa as verificações de tipo mais rigorosas.
- **`target: esnext`** — Gera código usando os recursos mais recentes do JavaScript.

---

## ▶️ Como rodar o projeto

**1. Clone o repositório e entre na pasta**
```bash
git clone <url-do-repositorio>
cd rocketlog
```

**2. Instale as dependências**
```bash
npm install
```

**3. Inicie o servidor em modo de desenvolvimento**
```bash
npm run dev
```

O servidor vai rodar em: **http://localhost:3333**

---

## 📜 Scripts

| Comando | O que faz |
|---|---|
| `npm run dev` | Inicia o servidor com o `tsx` em modo *watch* (reinicia sozinho ao salvar um arquivo). |

---

## 👩‍💻 Autora

Feito por **Isabela Alves** — [@isalvesdev](https://github.com/isalvesdev)
