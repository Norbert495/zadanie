# zadanie

- Zadanie polega na stworzeniu prostego formularza
- Formularz składa się z pól `email` i `password` i przycisku `submit`
- Po przesłaniu danych należy wyświetlić informację o sukcesie / błędzie.

### Elementy brane pod uwagę
- wybór i właściwie wykorzystnie elementów [kendo](https://www.telerik.com/kendo-vue-ui)
- czytelny i dobrze napisany kod
- estetyczny layout
- komunikację (bezpośredniość i transparentność)

### Uwagi
- Zadanie powinno zająć ok. 4h
- Pełna dowolność w realizacji

## API

*Example request*
```
POST https://dogz.studio/api/login

{
  email: 'join@dogz.studio',
  password: 'secret'
}
```
*Example response*
```
{
  message: 'Login success!',
  token: 'eyJhbGciOiJIUz...'
}
```

Aby otrzymać komunikat o błędzie, trzeba w polu `password` wpisać `error`

*Example request*
```
POST https://dogz.studio/api/login
{
  email: 'join@dogz.studio',
  password: 'error'
}
```
*Example response*
```
{
  message: 'Wrong password!',
  error: true
}
```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
