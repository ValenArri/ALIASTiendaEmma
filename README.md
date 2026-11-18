# Tienda Emma — Formas de pago

Página web de una sola pantalla donde los clientes copian el alias para transferir
y los lleva a Mercado Pago.

No necesita instalar nada. Archivos:

| Archivo      | Qué es                                                        |
| ------------ | ------------------------------------------------------------- |
| `index.html` | la página con los alias (es la que ven los clientes)           |
| `qr.html`    | cartel con el QR, listo para imprimir o descargar              |
| `qr.png`     | el QR en 1080 × 1080, para WhatsApp e Instagram                |
| `qr.svg`     | el QR vectorial, para carteles grandes sin perder calidad      |

Online: **https://valenarri.github.io/ALIASTiendaEmma/**
Cartel del QR: **https://valenarri.github.io/ALIASTiendaEmma/qr.html**

---

## Cómo cambiar los alias y los textos

1. Abrí `index.html` con el Bloc de notas (o cualquier editor).
2. Buscá el bloque que dice **`EDITÁ SOLO ESTE BLOQUE`** (está cerca del final).
3. Cambiá lo que necesites y guardá.

### Agregar un alias nuevo

Copiá uno de los bloques enteros y pegalo abajo, separado por una coma:

```js
{
  nombre: "Lemon",                  // nombre de la billetera o banco
  etiqueta: "Tienda",               // el cartelito verde chico ("" para ocultarlo)
  titular: "Titular: Tienda Emma",  // a nombre de quién está la cuenta
  alias: "emma.2130.lemon",         // el alias que se copia
  cvu: ""                           // opcional: CVU/CBU largo, con su propio botón
}
```

### Borrar un alias

Borrá el bloque `{ ... }` completo, junto con la coma que lo separa del siguiente.

### El botón de Mercado Pago

Desde el celular intenta abrir **la app** de Mercado Pago. Si no está instalada,
cae solo en la página web. Desde una computadora abre siempre la web.

**Esta página nunca se reemplaza.** El cliente salta a la app, y cuando vuelve al
navegador sigue teniendo los alias a mano.

- **Android**: el botón es un link a un *intent* apuntado al paquete
  `com.mercadopago.wallet`, y se abre en una pestaña aparte. Decide el propio
  navegador: si la app está la abre, y si no está usa el link de respaldo
  (que carga en esa pestaña nueva, no en la nuestra).
- **iPhone**: abre `mercadopago://` sin moverse de la página. Si en un segundo y
  medio seguimos acá, es que la app no está: en vez de llevarte a ningún lado,
  avisa *"No encontramos la app, tocá de nuevo"*, y el segundo toque abre la web
  en una pestaña aparte.

> En un iPhone **sin** la app instalada, Safari a veces muestra un cartel de error.
> Si te molesta, poné `appScheme: ""` en el bloque editable: el iPhone va derecho
> a la web (siempre en pestaña aparte) y el cartel no aparece más.

En `mercadoPago.url` podés poner:

- **Tu link de pago**: `https://link.mercadopago.com.ar/tuusuario` — el cliente paga directo.
- **La home de Mercado Pago**: `https://www.mercadopago.com.ar/` — el cliente pega el alias a mano. Es lo que está puesto ahora.

### Numeración de los alias

Los números (1, 2, 3…) se ponen solos según el orden de la lista `alias`.
Si agregás, sacás o reordenás uno, se renumeran automáticamente.

### Botón de WhatsApp

Está apagado. Para prenderlo, cambiá `activo: false` por `activo: true` y poné tu
número con código de país, sin `+` ni espacios ni guiones:

```js
whatsapp: {
  activo: true,
  numero: "5491122334455",
  ...
}
```

---

## Cómo publicarla gratis (GitHub Pages)

1. Subí los cambios a GitHub (`git push`).
2. En GitHub, entrá al repositorio → **Settings** → **Pages**.
3. En *Source* elegí **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y **Save**.
4. En un par de minutos queda publicada en:
   `https://valenarri.github.io/ALIASTiendaEmma/`

Ese link es el que les pasás a los clientes por WhatsApp o Instagram.

> **Importante:** el botón de copiar necesita `https://`. En GitHub Pages funciona
> siempre. Si abrís el archivo haciendo doble clic desde la PC puede que no copie;
> no es un error de la página.

---

## Probarla en tu computadora

Hacé doble clic en `index.html` y se abre en el navegador.
Se ve igual que publicada, pero el botón de copiar puede no andar (ver aviso de arriba).

---

## Si cambiás la dirección de la página

El QR apunta a `https://valenarri.github.io/ALIASTiendaEmma/`. Si algún día cambiás
el nombre del repositorio o le ponés un dominio propio, hay que generar el QR de nuevo
(los archivos `qr.png` y `qr.svg` quedan viejos y dejan de llevar al lugar correcto).

---

## Paleta

Tomada del logo de la tienda:

| Color             | Código    | Dónde se usa                        |
| ----------------- | --------- | ----------------------------------- |
| Turquesa          | `#26a79b` | cabecera, botones, detalles         |
| Turquesa oscuro   | `#166b63` | degradados, hover                   |
| Turquesa claro    | `#dcefec` | fondo de las cajas de alias         |
| Marrón            | `#3f2619` | textos, logo                        |
| Crema             | `#fbf7f2` | fondo de la página                  |

La página también se adapta sola al modo oscuro del celular.
