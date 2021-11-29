# React-JS Cocktails App with React Router and UseCallback

<br />

O projeto consome dados de um arquivo e renderiza os dados num cartão apresentando dados pessoais, especialmente idade e data de aniversário.

<br />

**Tendo sido adicionado ao projeto a funcionalidade de selecionar apenas os dados de aniversariantes do dia.**

<br />

#### React Project (the 15 Projects) - Freecodecamp.org

Conjunto de projetos de frontend inspirados na apresentação do professor **Johm Smilga** para aprofundar no conhecimento do framework React-JS e JavaScript. [^1]

<br />

[]()

<br />

### Imagem do card com Lista de Contatos:

![Imagem do card com Lista de Contatos](/public/images/lista-de-contatos.png)

<br />

### Imagem da funcionalidade acrescida de Aniversariantes do Dia:

![Imagem da funcionalidade acrescida de Aniversariantes do Dia](/public/images/aniversariantes-do-dia.png)

<br />

Abaixo temos o detalhe básico do código que estrutura o site com 03 rotas para páginas (Home, About e Single-Coctail), mais uma rota especial para tratamento de errors:

<br />

```
<Router>
    <Navbar />
        <Switch>
            <Route exact path="/">
                <Home />
            </Route>
            <Route path="/about">
                <About />
            </Route>
            <Route path="/cocktail/:id">
                <SingleCocktail />
            </Route>
            <Route path="*">
                <Error />
            </Route>
        </Switch>
    </Router>
```

<br />

<br />
<br />

[^1] John Smilga - Freecodecamp.org.
