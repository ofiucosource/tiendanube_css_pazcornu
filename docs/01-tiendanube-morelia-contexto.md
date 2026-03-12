# Tienda Nube + Morelia: contexto tecnico para CSS seguro

## Objetivo

Documentar el contexto oficial minimo necesario para editar CSS personalizado en una tienda Tienda Nube con template Morelia sin tocar hooks criticos del theme ni romper integraciones de precio, variantes, cuotas, envio o carrito.

## Hallazgos principales

- Morelia es una plantilla nativa de Tienda Nube.
- Su nombre interno es `morelia`.
- Su base tecnica oficial es grilla y utilities de Bootstrap 4.
- Los plugins mencionados oficialmente para Morelia son Lazysizes, Swiper y Fancybox.
- Tienda Nube recomienda usar el Theme Base como referencia tecnica porque los tutoriales y articulos estan basados en esa estructura.

## Lo mas importante para CSS personalizado

### 1. El CSS avanzado del admin ya esta pensado para sobreescribir el theme

En la documentacion de Layout, Tienda Nube indica que el contenido de `settings.css_code` se inyecta en el `layout.tpl` dentro de una etiqueta `<style>`. En terminos practicos:

- El CSS personalizado vive por encima del theme.
- Es valido apoyarse en overrides puntuales.
- Conviene priorizar selectores estables y evitar depender de jerarquias demasiado largas.

### 2. Los hooks no tienen todos el mismo nivel de estabilidad

Orden de confianza recomendado:

1. `data-store="..."`
2. Clases estructurales del componente documentado
3. Clases Bootstrap 4 de layout
4. Clases `js-...` solo para estilado no destructivo
5. Jerarquias fragiles basadas en wrappers transitorios

Lectura practica:

- `data-store` suele ser el mejor anchor para CSS duradero.
- Las clases `js-...` existen por comportamiento. Se pueden estilizar, pero no conviene cambiarles `display`, `position`, `overflow` o interaccion sin validar flujo completo.
- Las clases Bootstrap (`row`, `col`, `col-auto`, etc.) sirven de contexto, no deberian ser el selector principal de negocio.

### 3. Morelia comparte convenciones con Base y con otras plantillas nativas modernas

La documentacion oficial no publica una guia Morelia archivo por archivo. Lo que si confirma es:

- Morelia es nativa.
- Morelia comparte framework y stack con Rio, Lima, Cali, Uyuni, Toluca, Recife, Baires y otras plantillas modernas.
- Los articulos del Theme Base y Snipplets explican los mismos patrones de Product, Home, Shipping y Payments que aparecen reflejados en el CSS actual.

## Arquitectura oficial del theme

Segun "Estructura de Carpetas":

- `layouts/`: marco global, incluye head, header, footer y `template_content`.
- `templates/`: pantallas como `home.tpl`, `product.tpl`, `category.tpl`, `cart.tpl`.
- `snipplets/`: componentes reutilizables.
- `config/`: `settings.txt`, `sections.txt`, `translations.txt`, etc.
- `static/`: CSS, SCSS, JS, imagenes, checkout.

Impacto para nuestro caso:

- El CSS actual esta trabajando sobre componentes que normalmente nacen en `snipplets/product`, `snipplets/grid`, `snipplets/shipping`, `snipplets/payments` y `snipplets/page-header`.
- Eso hace posible mapear la mayoria de los selectores a piezas documentadas.

## Componentes oficiales relevantes para el CSS actual

### Product detail

La documentacion de Snipplets describe en `product-form.tpl` que el detalle de producto incluye:

- Header y breadcrumbs via `page-header.tpl`
- Precio dentro de `.price-container`
- Cuotas y medios de pago via `snipplets/payments/installments.tpl`
- Variantes via `product-variants.tpl`
- Cantidad via `product-quantity.tpl`
- CTA de compra via `.js-addtocart`
- Shipping calculator y sucursales via `shipping-calculator.tpl` y `branches.tpl`
- Descripcion dentro de `.product-description`

Ademas, los tutoriales de Shipping y de cuotas indican explicitamente que el contenedor padre del detalle suele ser:

```html
<div id="single-product" class="js-product-detail js-product-container ...">
```

Eso valida que `#single-product` sea un hook de alto valor para aislar estilos del detalle.

### Home y cards de producto

La documentacion de `home-featured-products.tpl` y `grid/item.tpl` confirma los siguientes anchors:

- `.section-featured-home`
- `.item-description`
- `.item-link`
- `.item-name`
- `.js-item-name`
- `data-store="product-item-name-..."`
- `.item-price-container`
- `.item-price`
- `data-store="product-item-price-..."`
- `.item-actions`
- `data-store="product-item-buy-button"`

Eso coincide casi uno a uno con el bloque Home del CSS actual.

### Variantes

En Base, `product-variants.tpl` documenta selects con `.js-variation-option` y grupos `.js-product-variants-group`.

En el CSS actual aparecen tambien `.btn-variant` y `.btn-variant-color`. Eso sugiere una capa de UI propia del theme Morelia o una customizacion previa sobre la interfaz de variantes.

Conclusion:

- `.js-product-variants-group` y `.form-label` tienen respaldo documental fuerte.
- `.btn-variant` y `.btn-variant-color` parecen hooks de interfaz del theme, validos pero con estabilidad media.

### Shipping

La documentacion de Shipping confirma anchors criticos como:

- `.js-free-shipping-message`
- `.js-shipping-calculator-label`
- `.js-shipping-calculator-label-default`
- `.js-shipping-input`
- `.js-calculate-shipping`
- `.js-shipping-calculator-response`
- `.js-store-branches-container`

Tambien indica que `shipping_options.tpl` y `shipping_suboptions` son usados por backend y no deben renombrarse ni moverse.

Para CSS esto significa:

- Se puede estilizar visualmente.
- No conviene ocultar o colapsar wrappers JS sin probar calculo de envio.

### Payments y discount disclaimer

Los articulos oficiales de cuotas y mensaje de descuento no combinable validan hooks como:

- `.js-product-payments-container`
- `.js-price-display`
- `.js-compare-price-display`
- `.js-product-discount-disclaimer`
- `.js-discount-explanation`

Son areas sensibles porque se actualizan con cambio de variante y promociones.

## Regla de oro para cambios sin errores

Si un selector afecta uno de estos grupos, probar siempre flujo completo:

- Precio
- Variante
- Cuotas
- Shipping
- CTA agregar al carrito
- Mensajes de stock

Grupos mas sensibles:

- `js-price-display`
- `js-compare-price-display`
- `js-product-payments-container`
- `js-product-variants-group`
- `js-variation-option`
- `js-quantity-*`
- `js-addtocart`
- `js-shipping-*`

## Criterio recomendado para futuras decisiones CSS

### Seguro

- Tipografia
- Color
- espaciado
- border
- hover
- letter-spacing
- text-transform
- opacidad
- micro-transiciones

### Requiere validacion funcional

- `display`
- `visibility`
- `position`
- `overflow`
- `pointer-events`
- `height` fija en modulos dinamicos
- reordenamiento visual de formularios

### Evitar salvo necesidad real

- ocultar clases `js-...`
- depender de nodos muy internos no documentados
- usar selectores excesivamente largos con muchos wrappers
- estilizar contra texto literal o contenido dinamico

## Relacion con la estetica actual

El CSS actual ya va en una direccion compatible con una referencia editorial tipo Zara:

- paleta neutra
- mucho blanco
- negro como ancla
- mayusculas finas
- bordes rectos
- poco adorno

Eso significa que la evolucion puede hacerse refinando proporciones y ritmo, no rehaciendo todo el lenguaje visual.

## Fuentes oficiales consultadas

- https://docs.tiendanube.com/help
- https://docs.tiendanube.com/help/nuestro-codigo
- https://docs.tiendanube.com/help/qu-es-twig
- https://docs.tiendanube.com/help/codigo-objetos
- https://docs.tiendanube.com/help/acerca-del-theme-base
- https://docs.tiendanube.com/help/theme-base
- https://docs.tiendanube.com/help/estructura-de-carpetas
- https://docs.tiendanube.com/help/layouts
- https://docs.tiendanube.com/help/snipplets
- https://docs.tiendanube.com/help/sections
- https://docs.tiendanube.com/help/templates-home
- https://docs.tiendanube.com/help/otras-plantillas-nativas-de-tiendanube
- https://docs.tiendanube.com/help/calculador-de-envos
- https://docs.tiendanube.com/help/informacin-de-medios-de-pago-y-cuotas-jq-nuvem
- https://docs.tiendanube.com/help/mensaje-de-descuento-sobre-precio-no-combinable

## Conclusiones accionables

- Podemos seguir trabajando sobre `#single-product` y `.section-featured-home` con buen margen de seguridad.
- Conviene preferir `data-store` y clases documentadas del componente antes que wrappers circunstanciales.
- Los hooks de precio, cuotas, variantes y envio deben tratarse como zonas funcionales, no solo esteticas.
- Morelia no tiene una guia publica tan granular como Base, por eso la referencia tecnica correcta es Base + Snipplets + tutoriales de funcionalidades + inspeccion del DOM real.