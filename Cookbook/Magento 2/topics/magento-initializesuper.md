## Método initialize
Por padrão, quando um componente js é invocado, o método initialize é chamado.

### Exemplo:
```javascript
initialize: function() {
    console.log("SayHi"); // Será acionado
}
```

## Método _super
The _super() method calls the parent UI component method with the same name as the _super() method’s caller. If that method does not exists in the parent UI component, then the method tries to find it higher in the inheritance chain.

```javascript
initialize: function () {
    this._super(); //_super will call parent's `initialize` method here

    return this;
}
```