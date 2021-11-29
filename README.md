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

### Imagem da página Home do Cocktails App:

![Imagem da página Home do Cocktails App](/public/images/reactjs-cocktails-with-router-app-01.png)

<br />

### Imagem da pagina /about construída com o pacote React-router-dom:

![Imagem da pagina /about construída com o pacote React-router-dom](/public/images/reactjs-cocktails-with-router-app-02.png)

<br />

### Imagem do sistema de busca feito na API de dados:

![Imagem do sistema de busca feito na API de dados](/public/images/reactjs-cocktails-with-router-app-03.png)

<br />

### Imagem da pagina /cocktail/:id construída com o pacote React-router-dom:

![Imagem da pagina /cocktail/:id construída com o pacote React-router-dom](/public/images/reactjs-cocktails-with-router-app-04.png)


<br />

### Imagem da pagina de erro construída com o pacote React-router-dom:

![Imagem da pagina de erro construída com o pacote React-router-dom](/public/images/reactjs-cocktails-with-router-app-05.png)


<br />

### Imagem do **warning** do React com relação à chamada da requisição da API em um hook useEffect:

![Imagem do **warning** do React com relação à chamada da requisição da API](/public/images/lidar com o Warning para Fetch no projeto React.png)

<br />

O problema foi sanado envelopando a função de fecth dos dados em um useCallback, porque a inserção da função diretamente no Array de Depenência do useEffect responsável por chamar a função criaria um loop infinito:

<br />

```
const fetchDrinks = useCallback(async () => {
    setLoading(true);

    try {
      const response = await fetch(`${url}${searchTerm}`);
      const data = await response.json();

      console.log(data);
      const { drinks } = data;

      if (drinks) {
        const newCocktails = drinks.map((drink) => {
          const { 
            idDrink,
            strDrink,
            strDrinkThumb,
            strAlcoholic,
            strGlass
          } = drink;

          return {
            id: idDrink,
            name: strDrink,
            image: strDrinkThumb,
            info: strAlcoholic,
            glass: strGlass,
          };
        });

        setCocktails(newCocktails);
      } else {
        setCocktails([]); 
      } 

      setLoading(false);
    } catch (error) {
      console.log(error);
      setLoading(false);
    }
  }, [searchTerm]);


  useEffect(() => {
    fetchDrinks();
  }, [searchTerm, fetchDrinks]);
```


<br />


Abaixo temos o detalhe básico do código que estrutura o site com 03 rotas para páginas (Home, About e Single-Coctail), mais uma rota especial para tratamento de errors, montado com a biblioteca React-router-dom:

<br />

```
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

...outros códigos

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

Agora nós vemos abaixo como funciona o sistema de roteamento da biblioteca React-router-dom com o uso de Links:

<br />

```
import { Link } from 'react-router-dom';

...outros códigos

<nav className="navbar">
    <div className="nav-center">
    <Link to="/">
        <img src={logo} alt="cocktail db logo" className="logo" />
    </Link>
    <ul className="nav-links">
        <li>
        <Link to="/">
            Home
        </Link>
        </li>
        <li>
        <Link to="/about">
            About
        </Link>
        </li>
    </ul>
    </div>
</nav>
```

<br />

<br />
<br />

[^1] John Smilga - Freecodecamp.org.
