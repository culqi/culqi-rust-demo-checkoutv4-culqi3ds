# DEMO - Culqi RUST + Checkout V4 + Culqi 3DS

La demo integra Culqi RUST, Checkout V4 , Culqi 3DS y es compatible con la v2.0 del Culqi API, con esta demo podrás generar tokens, cargos, clientes, cards.

## Requisitos

- Rust 1.60.0+
- Afiliate [aquí](https://afiliate.culqi.com/).
- Si vas a realizar pruebas obtén tus llaves desde [aquí](https://integ-panel.culqi.com/#/registro), si vas a realizar transacciones reales obtén tus llaves desde [aquí](https://mipanel.culqi.com/#/registro).

> Recuerda que para obtener tus llaves debes ingresar a tu CulqiPanel > Desarrollo > ***API Keys***.

![alt tag](http://i.imgur.com/NhE6mS9.png)

> Recuerda que las credenciales son enviadas al correo que registraste en el proceso de afiliación.

* Para encriptar el payload debes generar un id y llave RSA  ingresando a CulqiPanel > Desarrollo  > RSA Keys.

## Instalación

Ejecuta los siguientes comandos:

```bash
cargo build
```

## Configuración backend

En **src/main.rs**, reemplaza los placeholders por tus llaves de prueba. Usa una llave pública `pk_test_` y una llave privada `sk_test_`; la llave privada solo debe usarse en el backend.

```rust
let pk = "INSERTE_SU_LLAVE_PUBLICA";
let sk = "INSERTE_SU_LLAVE_PRIVADA";
```

No hagas commit de tus llaves.

## Configuración frontend
Para configurar los datos del cargo, la llave pública, el `rsa_id`, la llave RSA pública y los datos del cliente, modifica `static/js/config/index.js`. Usa tu llave pública `pk_test_` y las credenciales RSA generadas desde CulqiPanel.

```js
export default Object.freeze({
  TOTAL_AMOUNT: 600,
  CURRENCY: "PEN",
  PUBLIC_KEY: "INSERTE_SU_LLAVE_PUBLICA",
  COUNTRY_CODE: "PE",
  RSA_ID: "INSERTE_SU_RSA_ID",
  RSA_PUBLIC_KEY: "INSERTE_SU_LLAVE_RSA",
});
```

No hagas commit de llaves. La demo realiza llamadas reales a Culqi; configura tus propias llaves de prueba antes de usarla.

## Inicializar la demo
Ejecutar el siguiente comando:

```bash
cargo run
```

## Probar la demo

Para poder visualizar el frontend de la demo ingresar a la siguiente URL:

- Para probar cargos: http://localhost:3030/index.html
- Para probar creación de cards: http://localhost:3030/index_card.html

## Documentación

- [Referencia de Documentación](https://docs.culqi.com/)
- [Referencia de API](https://apidocs.culqi.com/)
