# App Gerencial (HTML + TailwindCSS + JavaScript)

Este repositório contém um **aplicativo gerencial** básico, desenvolvido puramente com **HTML**, **TailwindCSS** e **JavaScript** (sem uso de frameworks modernos como React/Vue). O foco principal é demonstrar **layout responsivo** em tons de **roxo**, com funcionalidade CRUD em diversas telas:

- **Tela de Login** (`index.html` ou `login.html`)  
- **Tela de Dashboard** (`dashboard.html`) - exibe gráficos e dados gerenciais  
- **Tela de Clientes** (`clientes.html`) - CRUD de clientes, modal de cadastro  
- **Tela de Estoque** (`estoque.html`) - exibe produtos em **cards** + modal de “novo produto”  
- **Tela de Vendas** (`vendas.html`) - registra vendas com modal de “nova venda”

## Estrutura dos Arquivos

```
/
├─ index.html (ou login.html)
├─ dashboard.html
├─ clientes.html
├─ estoque.html
├─ vendas.html
├─ README.md
└─ ...
```

### `index.html` (Tela de Login)
- **Layout roxo** para fundo e header.
- Formulário com **campo de usuário/e-mail** e **senha**.
- **Validação simples** em JavaScript.
- Responsivo graças ao **TailwindCSS**.

### `dashboard.html`
- **Navbar** fixa, visível em todas as telas, contendo links para `Dashboard`, `Estoque`, `Clientes`, `Vendas`.
- Seção de **gráficos** usando **[Chart.js](https://www.chartjs.org/)** (CDN), demonstrando exemplo de “Vendas no Mês” e “Produtos Mais Vendidos”.
- Tabela de **clientes inadimplentes** como exemplo adicional de dados gerenciais.
- **Responsividade** feita com **classes utilitárias** do Tailwind (`grid-cols-1`, `md:grid-cols-2`, etc.).

### `clientes.html`
- **Navbar** padrão (repetida em todas as telas para padronização).
- **Tabela** de clientes com colunas (Nome, Telefone, E-mail, Status, Ações).
- Botão **“Novo Cliente”** abre um **modal** para cadastrar cliente.  
- Campo de **busca** para filtrar clientes diretamente no front-end (JS).  
- Layout roxo e responsivo (Tailwind).

### `estoque.html`
- **Exibe produtos em formato de cards** em um **grid responsivo** (`grid-cols-1 sm:grid-cols-2 lg:grid-cols-4`).
- Cada card mostra **foto genérica**, **nome do produto**, **quantidade**, **preço** e botões de **Editar** / **Excluir**.
- Botão **“Novo Produto”** abre modal para adicionar um novo item no estoque.
- A funcionalidade do modal simula um “CRUD” front-end, sem backend real (mas pode ser facilmente adaptado para API externa).

### `vendas.html`
- Tabela com **histórico de vendas** (Produto, Cliente, Valor Total, Entrada, Parcelas).
- Botão **“Nova Venda”** abre modal que pede **produto**, **cliente**, **valor**, **valor de entrada**, **parcelas** e **observações**.
- Ao salvar, é adicionada uma nova linha na tabela.

---

## Como a Responsividade Foi Feita

Todos os arquivos usam **[TailwindCSS](https://tailwindcss.com/)**, importado via CDN. A responsividade se dá por:

1. **Classes responsivas** do Tailwind (ex.: `grid-cols-1 sm:grid-cols-2 lg:grid-cols-4`) que ajustam a quantidade de colunas e layout de acordo com o tamanho da tela.  
2. **`max-w-*`, `w-full`, `h-full`** para permitir que elementos (inputs, containers, etc.) se ajustem ao espaço disponível.  
3. **Media Queries internas do Tailwind** (por exemplo, `sm:`, `md:`, `lg:`) definindo breakpoints.  
4. **Meta Tag `viewport`** em cada arquivo HTML, permitindo correto escalonamento em telas móveis:

   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
   ```

5. **Grid + Flexbox** utilitários (ex.: `flex`, `items-center`, `justify-between`) para organizar conteúdo adaptativamente.  

Todos esses fatores contribuem para que o layout funcione bem em **celulares, tablets e desktops**.

---

## Fluxo / Arquitetura Geral

Este projeto **não** usa backend de forma real; todos os dados de **clientes, estoque, vendas** são simulados no **front-end** com **inserção dinâmica** no DOM. Em produção, cada ação (Criar, Editar, Excluir) chamaria uma **API** (REST ou GraphQL) para persistência no banco de dados. 

### Possível Arquitetura em Produção

1. **Front-end**: as páginas HTML + Tailwind + JS, rodando no navegador, fazem requisições `fetch()` para um servidor back-end.  
2. **Back-end**: poderia ser feito em Node.js, Python, Java, etc., expondo endpoints `GET /api/clientes`, `POST /api/vendas`, etc.  
3. **Banco de Dados**: MySQL, PostgreSQL ou outro, armazenando os dados de maneira persistente.

Atualmente, o projeto é **estático** e foca em demonstrar **layout** e **responsividade**.

---

## Futuras Integrações (Roadmap)

1. **Twilio para Realizar Cobranças**  
   - Integrar a [API do Twilio](https://www.twilio.com/docs) para enviar **SMS** ou **WhatsApp** a clientes inadimplentes.  
   - Ex.: ao adicionar um cliente como “Inadimplente” por mais de X dias, o sistema automaticamente dispara notificação via Twilio.

2. **API de Relatórios/BI**  
   - Conectar o dashboard a uma ferramenta de BI (ex.: **Looker Studio** ou **Power BI**).  
   - Expor endpoints no back-end para dados agregados de vendas/estoque e renderizar gráficos mais robustos.
   - Ou integrar com **Chart.js** de forma dinâmica (dados reais) ao invés de mock.

3. **Autenticação e Autorização**  
   - No login, efetuar validação real num servidor, gerar token (JWT) e proteger rotas (somente acessíveis se logado).
   - Sessões e cookies para controlar acesso.

4. **Upload de Imagens para Produtos**  
   - Permitir upload e armazenamento de fotos reais dos produtos, em vez de `placeholder.com`.

---

## Como Usar/Executar

Basta abrir os arquivos `*.html` no seu navegador (Chrome, Firefox, Edge, etc.). Não há necessidade de servidor, pois é um projeto estático.

1. **Tela de Login**: abra `index.html`. Informe usuário e senha (qualquer valor), clique em **Entrar**.  
2. **Dashboard**: acessível em `dashboard.html`. Mostra gráficos e tabela de inadimplentes.  
3. **Clientes**: acessível em `clientes.html`. Permite buscar, cadastrar novo cliente (abrindo modal).  
4. **Estoque**: acessível em `estoque.html`. Mostra itens em **cards**, com modal para inserir novo produto.  
5. **Vendas**: acessível em `vendas.html`. Historiza vendas, com modal para lançar vendas novas (produto, cliente, valor, parcelas).  

---



---

### Licença

Este projeto é livre para estudo e uso particular. Sinta-se à vontade para adaptá-lo a suas necessidades. Caso vá utilizá-lo comercialmente, considere manter as devidas referências aos autores das bibliotecas (Tailwind, Chart.js, etc.).

---

