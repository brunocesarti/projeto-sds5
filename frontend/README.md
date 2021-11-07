# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

# FLUXO DE DESENVOLVIMENTO DURANTE A SEMANA SPRING REACT

# ![DevSuperior logo](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/devsuperior-logo-small.png) Semana Spring React - Episódio 1
>  

## Realização
[DevSuperior - Escola de programação](https://devsuperior.com.br)

[![DevSuperior no Instagram](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/ig-icon.png)](https://instagram.com/devsuperior.ig)
[![DevSuperior no Youtube](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/yt-icon.png)](https://youtube.com/devsuperior)

## Objetivos do projeto para esta aula
- Criar projetos backend e frontend
- Salvar os projeto no Github em monorepo
- Montar o visual estático do front end
- Publicar o front end no Netlify

## Checklist

### Passo 0: preparação

- Dica: extensões do VS Code

- Criar pastas do projeto

![DevSuperior no Instagram](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/pastas-sds3.png)

- Conferir Yarn
```bash
yarn -v
npm install --global yarn
```

### Passo 1: criar projetos
- Criar projeto ReactJS com `create-react-app`:
```bash
npx create-react-app frontend --template typescript
```
- *Lembrete: excluir repositório Git do projeto ReactJS*
- Criar projeto Spring Boot no `Spring Initializr` com as seguintes dependências:
  - Web
  - JPA
  - H2
  - Postgres
  - Security
- Se tiver com erro no pom.xml, tentar:
  - Botão direito no projeto -> Maven -> Update project (force update)
  - Menu Project -> Clean
  - Apagar pasta .m2 e deixar o STS refazer o download
- **COMMIT: Project created**

- *Lembrete: ver extensões e arquivos ocultos*
- Salvar o projeto no seu Github
```bash
git config --global user.name <seu nome>
git config --global user.email <seu email>

git init

git add .

git commit -m "Project created"

git remote add origin <seu endereço>

git push -u origin main
```
### Passo 2: "limpar" o projeto ReactJS
- Limpar projeto ReactJS / tsconfig.json
- Arquivo _redirects
```
/* /index.html 200
```
- **COMMIT: Project clean**
### Passo 3: adicionar Bootstrap e CSS ao projeto
- Bootstrap
```
yarn add bootstrap
```
```
(index.tsx) import 'bootstrap/dist/css/bootstrap.css';
```
- Assets e CSS
```css
@import url('https://fonts.googleapis.com/css2?family=Ubuntu:wght@300;400;500;700&display=swap');
:root {
    --color-primary: #FF8400;
}

html, body {
    height: 100%;
    font-family: "Ubuntu", sans-serif;
}

#root {
    display: flex;
    flex-direction: column;
    height: 100%;
}

.content {
    flex: 1 0 auto;
}

.footer {
    flex-shrink: 0;
    text-align: center;
}

.bg-primary {
    background-color: var(--color-primary) !important;
}

.text-primary {
    color: var(--color-primary) !important;
}
```
```
(index.tsx) import 'assets/css/styles.css';
```
- **COMMIT: Bootstrap**
### Passo 4: adicionar componentes estáticos básicos
- Navbar
```html
<div className="d-flex flex-column flex-md-row align-items-center p-3 px-md-4 mb-3 bg-light border-bottom shadow-sm">
  <div className="container">
    <nav className="my-2 my-md-0 mr-md-3">
      <img src={ImgDsDark} alt="DevSuperior" width="120" />
    </nav>
  </div>
</div>
```
- Footer
```html
<footer className="footer mt-auto py-3 bg-dark">
  <div className="container">
    <p className="text-light">App desenvolvido por <a href="https://github.com/acenelio" target="_blank" rel="noreferrer">Nelio Alves</a></p>
    <p className="text-light"><small><strong>Semana Spring React</strong><br/>
      Evento promovido pela escola DevSuperior: <a href="https://instagram.com/devsuperior.ig" target="_blank" rel="noreferrer">@devsuperior.ig</a></small></p>
  </div>
</footer>
```
- DataTable
```html
<div className="table-responsive">
    <table className="table table-striped table-sm">
        <thead>
            <tr>
                <th>Data</th>
                <th>Vendedor</th>
                <th>Clientes visitados</th>
                <th>Negócios fechados</th>
                <th>Valor</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>22/04/2021</td>
                <td>Barry Allen</td>
                <td>34</td>
                <td>25</td>
                <td>15017.00</td>
            </tr>
        </tbody>
    </table>
</div>
```
- **COMMIT: Basic static components**
### Passo 5: adicionar gráficos estáticos
- Apex Charts
```bash
yarn add apexcharts
yarn add react-apexcharts
```
- BarChart
```javascript
const options = {
    plotOptions: {
        bar: {
            horizontal: true,
        }
    },
};

const mockData = {
    labels: {
        categories: ['Anakin', 'Barry Allen', 'Kal-El', 'Logan', 'Padmé']
    },
    series: [
        {
            name: "% Sucesso",
            data: [43.6, 67.1, 67.7, 45.6, 71.1]                   
        }
    ]
};
```
- DonutChart
```javascript
const mockData = {
    series: [477138, 499928, 444867, 220426, 473088],
    labels: ['Anakin', 'Barry Allen', 'Kal-El', 'Logan', 'Padmé']
}

const options = {
    legend: {
        show: true
    }
}
```
- **COMMIT: Static charts**
### Passo 6: implantação no Netlify
- Deploy básico
  - Base directory: frontend
  - Build command: yarn build
  - Publish directory: frontend/build

- Configurações adicionais
  - Site settings -> Domain Management: (colocar o nome que você quiser)
  - Deploys -> Trigger deploy

## PARABÉNS!

![Parabéns!](https://raw.githubusercontent.com/devsuperior/bds-assets/main/img/trophy.png)

- Quero muito saber seu feedback
  - O que você está achando da nossa abordagem?
  - Você está conseguindo acompanhar?
  - O que você está achando do evento?
- Participe
  - Comente na página da Semana Spring React
  - Divulgue seu projeto no Linkedin e marque a DevSuperior