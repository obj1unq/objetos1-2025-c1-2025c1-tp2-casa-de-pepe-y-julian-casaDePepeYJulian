# Casa de Pepe y Julián (Con colecciones y errores)

Pepe y Julián viven juntos, y nos pidieron que les ayudemos con un sistema para administrar los gastos de la casa.

> **Aclaración**: Para este enunciado se pide tanto la implementación de los objetos que resuelven los requerimientos planteados, como los tests descriptos en los _casos de prueba_ como mínimo (si quieren hacer más tests también son bienvenidos).

## Sobre las cosas que se compran

De cada cosa nos interesa el precio y su categoría, que puede ser electrodoméstico, comida o mueble (pero podría haber otras).

En este modelo reducido, vamos a considerar las siguientes cosas que podrían ser interesantes para comprar: 
- una heladera que vale 20000 pesos y es un electrodoméstico 
- una cama que sale 8000 y es un mueble
- una tira de asado que sale 350 pesos y es comida
- un paquete de fideos que sale 50 pesos y es comida
- una plancha que vale 1200 pesos y es un electrodoméstico

Implementar, además de los objetos que representan cada cosa, un objeto que represente a la casa, que entienda los siguientes mensajes:
- `comprar(cosa)`: registra que se ha comprado una cosa.
- `cantidadDeCosasCompradas()`: indica ... eso.
- `tieneAlgun(categoria)`: indica si compró algo que es corresponde a esa categoría alguna vez.
- `vieneDeComprar(categoria)`: indica si la _última_ cosa que se compró es de la categoría indicada.
- `esDerrochona()`: indica si el importe total de las cosas compradas es de 9000 pesos o más.
- `compraMasCara()`: retorna la cosa comprada de mayor valor.
- `comprados(categoría)`: devuelve todas las cosas compradas de la categoría dada. 
- `malaEpoca()`: indica si todas las cosas compradas son comida.
- `queFaltaComprar(lista)`: recibe una lista de cosas y devuelve las cosas de esa lista que aún no se han comprado. <br>
  **Atención**: es una pregunta. No se pide que se compren. 
- `faltaComida()`: indica si se han comprado menos de 2 cosas que son comida.
-  categoríasCompradas(): indica todas las categorías para las cuales se ha realizado al menos una compra

### Ejemplo

Hacer que se compre una heladera, una cama y una placha.
verificar que:
- la lista de las cosas compradas es heladera, cama y plancha
- cantidad de cosas compradas es 3
- tiene algún electrodoméstico
- tiene algún mueble
- no tiene alguna comida
- Si le preguntan si viene de comprar un electrodoméstico dice que sí, pero si le preguntan si viene de comprar un mueble dice que no
- Es derrochona (ya que gastó 29200)
- los electrodomésticos compramos son la heladera y la plancha
- los muebles comprados son: la cama y nada más
- no hay comida comprada
- no es una mala época
- si le preguntamos que falta comprar de una tira de asado, una plancha y un paquete de fideos debe contestar que falta la tira de asado y el paquete de fideos.
- falta comida
- las categorías compradas son electrodoméstico y mueble

## Cuentas bancarias
Pepe y Julián poseen varios tipos de cuentas bancarias, de las cuales pueden conocer su saldo y extraer y depositar dinero. 
Estas 2 son las posibles cuentas que pueden configurar para la casa:

1. Una **cuenta corriente**, mantiene un saldo, al depositar suma el saldo, al extraer lo resta. No permite tener saldo negativo. 
> **Caso de Prueba**: si la cuenta tiene 20 de saldo, si se deposita 1000 pesos, el saldo queda en 1020 pesos, si luego se extraen 50 queda en 970 pesos. Si se intenta extraer 2000 debería lanzar error ya que no se puede cumplir la responsabilidad.
2. Una **cuenta con gastos**, también mantiene un saldo y, además, un costo por operación. Al depositar suma al saldo el importe indicado menos el costo por operación. Al extraer resta el saldo normalmente. Permite tener saldo negativo, pero no deja que se deposite más de 1000 pesos de una vez.
> **Caso de Prueba**: para una cuenta con un saldo de 500 pesos y 20 pesos de costo por operación, si se deposita 1000 pesos, el saldo queda en 1480 pesos. Si luego se extrae 30, queda en 1450. Después se eso se intenta depositar 2000, pero no se puede porque violaría la regla de negocio, por lo que hay que verificar que se lance el error y que el saldo siga siendo de 1450. Finalmente se extraen 2000 pesos dejando el saldo en -550.

Ellos asignan una de esas cuentas para gestionar los gastos de la casa. Cada vez que se preduce un gasto en la casa, se extrae de la cuenta asignada el importe correspondiente.

### Se pide que al comprar una cosa  eso se vea afectado en la cuenta elegida previamente.
 Ejemplo: Si la casa tiene configurada una cuenta corriente con saldo 1000, se compra una tira de asado y un paquete de fideos, entonces la cuenta corriente queda con saldo 600.
¿Qué pasa si la cuenta era la Cuenta Corriente y se compra superando el saldo? Si se realiza una compra en este caso ¿debería quedar en la lista de compras dicha cosa? ¿Cómo se soluciona este problema?
 
