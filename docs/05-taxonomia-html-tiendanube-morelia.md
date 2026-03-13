# Taxonomia HTML de Tiendanube con foco en Morelia

## Objetivo

Construir una referencia operativa para editar CSS con mayor precision en Tiendanube, entendiendo:

- que etiquetas HTML aparecen de forma recurrente en los templates nativos
- que bloques existen por pantalla
- que anchors son oficialmente estables
- donde termina lo verificado y donde empieza la inferencia o la inspeccion puntual del DOM

## Alcance real

### Verificado

- Tiendanube documenta la estructura de `layout.tpl`, `templates`, `snipplets`, `sections`, objetos Twig y muchos fragmentos reales de HTML del Theme Base.
- Tiendanube confirma que Morelia es una plantilla nativa, codename `morelia`, construida sobre grilla y utilities de Bootstrap 4, con Lazysizes, Swiper y Fancybox.
- Tiendanube documenta `data-store` como contrato oficial de anclaje para aplicaciones y agentes externos.
- Tiendanube documenta componentes privados que pueden renderizar parte del markup sin exponer su codigo editable.

### No verificado de forma exhaustiva

- No existe una fuente oficial que enumere todas las etiquetas HTML posibles de Morelia en todos los estados, configuraciones y combinaciones de contenido.
- No puede asumirse que todas las tiendas con Morelia mantengan markup identico si hubo customizaciones por FTP o cambios previos.

## Lectura correcta de este documento

Este archivo no debe leerse como un snapshot literal del DOM final de una tienda.

Debe leerse como:

1. taxonomia oficial de bloques y componentes
2. inventario de etiquetas recurrentes publicadas por Tiendanube
3. mapa de anchors estables para CSS durable
4. guia para saber que conviene inspeccionar en preview antes de abrir selectores nuevos

## Capa 1: esqueleto global del documento

Segun la documentacion oficial de `layout.tpl`, el storefront nativo de Tiendanube abre y organiza el documento con estas etiquetas base:

- `<!DOCTYPE html>`
- `<html>`
- `<head>`
- `<meta>`
- `<link>`
- `<title>`
- `<style>`
- `<script>`
- `<body>`

Implicancia CSS:

- El CSS avanzado del administrador entra en un `<style>` renderizado desde `settings.css_code`.
- El `head` incluye OG tags, Twitter tags, structured data y preload/lazy strategies.
- No conviene construir CSS apoyado en metadata o scripts; la capa util para estilado arranca en `body`, `header`, `footer`, `section`, `div`, formularios y componentes.

## Capa 2: templates por pantalla

## 1. Layout compartido

Bloques estructurales documentados:

- `header`
- `footer`
- contenido variable inyectado por `{% template_content %}`

Anchors oficiales relevantes:

- `data-store="head"`
- `data-store="navigation"`
- `data-store="account-links"`
- `data-store="page-title"`
- `data-store="footer"`
- `data-store="newsletter-form"`

Etiquetas recurrentes verificadas:

- `header`
- `footer`
- `div`
- `nav` no siempre aparece explicitamente en snippets publicados, pero la navegacion se organiza como listas y wrappers dentro del header
- `ul`
- `li`
- `a`
- `form`
- `input`
- `button`
- `img`
- `svg`

## 2. Home

### Bloques que Morelia puede incluir oficialmente

Segun `puntos de anclaje para aplicaciones`, Morelia puede tener estos modulos de home:

- `data-store="home-image-text-module"`
- `data-store="home-categories-featured"`
- `data-store="home-welcome-message"`
- `data-store="home-institutional-message"`
- `data-store="home-products-featured"`
- `data-store="home-products-new"`
- `data-store="home-products-sale"`
- `data-store="home-products-promotion"`
- `data-store="home-product-main"`
- `data-store="home-video"`
- `data-store="home-brands"`
- `data-store="home-testimonials"`
- `data-store="home-newsletter"`
- `data-store="home-instagram-feed"`
- `data-store="banner-services"`

### Etiquetas HTML recurrentes en home

Verificadas en snippets oficiales:

- `section`
- `div`
- `h1`
- `h2`
- `h3`
- `p`
- `a`
- `button`
- `img`
- `svg`

Patrones frecuentes:

- carruseles: `section > div > div.swiper-container > div.swiper-wrapper > div.swiper-slide`
- banners y modulos: combinaciones de `section`, `div`, `a`, `img`, `h1`, `p`, `button`
- listados de productos: reutilizan el item de producto del grid, no un HTML totalmente distinto

Observacion operativa:

- En home, la presencia de modulos depende fuertemente de `settings` y de que el comerciante los tenga activados.
- No todo bloque disponible en Morelia esta siempre presente en una tienda real.

## 3. Listados: categoria, subcategoria, coleccion y busqueda

Bloques oficiales:

- page header
- banner de categoria
- filtros
- sort-by
- grilla de productos
- paginacion o scroll infinito

Anchors oficiales fuertes:

- `data-store="filters-nav"`
- `data-store="filters-group"`
- `data-store="product-item-{{ product.id }}"`
- `data-store="product-item-image-{{ product.id }}"`
- `data-store="product-item-info-{{ product.id }}"`
- `data-store="product-item-name-{{ product.id }}"`
- `data-store="product-item-price-{{ product.id }}"`
- `data-store="category-grid-{{ category.id }}"`

Etiquetas HTML recurrentes verificadas:

- `section`
- `div`
- `ul`
- `li`
- `a`
- `label`
- `input`
- `select`
- `option`
- `img`
- `button`
- `h6`
- `span`

Observacion operativa:

- El item del producto es el bloque clave del CSS reutilizable entre home, categorias, relacionados y search.
- Filtros y sort pueden renderizarse con `label`, `input[type=checkbox]`, `select`, `option`, listas y wrappers de acordeon.
- En tiendas nuevas tambien pueden aparecer componentes privados para filtros y ordenamiento, por lo que la estructura interna puede cambiar mas que el anchor padre.

## 4. Detalle de producto

Bloques oficiales documentados:

- contenedor general del detalle
- galeria / slider de imagenes
- header con breadcrumbs y nombre
- precio
- promociones
- cuotas
- variantes
- cantidad
- CTA agregar al carrito
- calculador de envios
- sucursales
- descripcion
- relacionados

Anchors oficiales fuertes:

- `data-store="product-detail"`
- `data-store="product-image-{{ product.id }}"`
- `data-store="product-info-{{ product.id }}"`
- `data-store="product-name-{{ product.id }}"`
- `data-store="product-price-{{ product.id }}"`
- `data-store="product-form-{{ product.id }}"`
- `data-store="product-description-{{ product.id }}"`
- `data-store="related-products"`
- `data-store="shipping-calculator"`

Etiquetas HTML recurrentes verificadas:

- `div`
- `section`
- `h1`
- `h4`
- `h5`
- `p`
- `span`
- `strong`
- `small`
- `a`
- `form`
- `input`
- `button`
- `label`
- `select`
- `option`
- `ul`
- `li`
- `img`
- `meta`
- `script`

Notas por subcomponente:

### Galeria de producto

Etiquetas publicadas:

- `div`
- `a`
- `img`

Patron frecuente:

- Swiper usa wrappers `swiper-container`, `swiper-wrapper`, `swiper-slide`

### Precio y cuotas

Etiquetas publicadas:

- `div`
- `span`
- `h4`
- `a`
- `strong`
- `ul`
- `li`
- `table`
- `thead`
- `tbody`
- `tr`
- `th`
- `td`

Observacion:

- En la plataforma actual, parte de esta zona puede venir de componentes privados o de snippets historicos. El anchor suele ser mas confiable que la jerarquia interna.

### Variantes y cantidad

Etiquetas publicadas:

- `div`
- `label`
- `select`
- `option`
- `input`
- `span`

Observacion:

- Si una tienda usa UI custom de variantes tipo botones de color, puede haber capas visuales adicionales no exhaustivamente documentadas en Base.

### Shipping y sucursales

Etiquetas publicadas:

- `div`
- `span`
- `a`
- `button`
- `ul`
- `li`
- `label`
- `input`
- `strong`
- `h6`
- `select`
- `option`

Observacion:

- Es una de las zonas mas sensibles del theme.
- No se recomienda tratarla como un bloque puramente visual porque el backend inyecta resultados y estados.

### Descripcion

Etiquetas publicadas:

- `div`
- `h5`
- HTML libre cargado por el vendedor dentro de `product.description`

Consecuencia:

- Dentro de `.product-description` puede aparecer HTML editorial no controlado por el theme: `p`, `strong`, `em`, `ul`, `ol`, `li`, `a`, `img`, etc.
- Aca conviene usar reglas tipograficas contenidas y no suponer una estructura unica.

## 5. Carrito

Bloques oficiales:

- listado de items
- subtotal
- promociones
- calculador de envios
- sucursales
- total
- cuotas del carrito
- CTA checkout

Anchors oficiales fuertes:

- `data-store="cart-page"`
- `data-store="cart-form"`
- `data-store="cart-item-{{ item.product.id }}"`
- `data-store="cart-total"`
- `data-store="shipping-caculator"`

Etiquetas HTML recurrentes verificadas:

- `div`
- `form`
- `input`
- `button`
- `a`
- `img`
- `h2`
- `h5`
- `h6`
- `small`
- `strong`
- `span`
- `ul`
- `li`
- `label`

Observacion:

- El carrito mezcla markup propio del template con resultados de shipping inyectados por backend.
- CSS demasiado agresivo sobre `form`, `row`, `input` o `button` puede romper tanto popup cart como cart page.

## 6. Cuenta de usuario

Pantallas oficiales:

- login
- register
- info
- address
- addresses
- order
- orders
- newpass
- reset

Anchors oficiales:

- `data-store="account-login"`
- `data-store="account-register"`
- `data-store="account-orders"`
- `data-store="account-order-item-{{ order.id }}"`
- `data-store="account-order-detail-{{ order.id }}"`

Etiquetas HTML recurrentes verificadas o fuertemente esperables por snippets oficiales:

- `section`
- `div`
- `h1`
- `h4`
- `h5`
- `p`
- `form`
- `label`
- `input`
- `select`
- `option`
- `button`
- `a`
- `table`
- `tr`
- `td`

## 7. Contacto y paginas internas

Bloques oficiales:

- page header
- contenido o formulario
- links de contacto

Anchor oficial confirmado:

- `data-store="contact-form"`

Etiquetas HTML recurrentes:

- `section`
- `div`
- `h1`
- `p`
- `form`
- `label`
- `input`
- `textarea`
- `button`
- `ul`
- `li`
- `a`

## 8. Password y 404

Estos templates existen oficialmente, pero su interes para CSS de catalogo suele ser menor.

Etiquetas recurrentes esperables por la arquitectura documentada:

- `html`
- `head`
- `body`
- `header`
- `footer`
- `section`
- `div`
- `h1`
- `p`
- `form` en password cuando aplica

## Capa 3: familias de etiquetas HTML realmente relevantes para CSS

## 1. Estructura

- `header`
- `footer`
- `section`
- `div`

Son la base de casi todos los wrappers de layout y componentes.

## 2. Navegacion y links

- `nav` cuando la plantilla lo expone explicitamente
- `ul`
- `li`
- `a`

Se usan en menus, breadcrumbs, filtros, footer nav, cuentas, sugerencias de busqueda y listas de productos.

## 3. Tipografia y contenido

- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `p`
- `span`
- `strong`
- `small`
- `i`

Son las etiquetas mas frecuentes para nombres, precios, subtitulos, avisos, cuotas, shipping y contenido editorial.

## 4. Formularios

- `form`
- `label`
- `input`
- `textarea`
- `select`
- `option`
- `button`

Zonas criticas:

- buscador
- variantes
- cantidad
- login y registro
- contacto
- calculador de envios
- carrito

## 5. Media

- `img`
- `svg`

La plataforma usa fuertemente imagenes responsive, lazy load y SVGs inline o incluidos por snipplets.

## 6. Tablas y datos complejos

- `table`
- `thead`
- `tbody`
- `tr`
- `th`
- `td`

Aparecen sobre todo en medios de pago, cuotas y promociones mas complejas.

## 7. Metadata no orientada a CSS

- `meta`
- `link`
- `script`
- `style`

Existen en el markup y son oficiales, pero rara vez son utiles para el problema de precision de CSS visual.

## Capa 4: anchors realmente seguros

Orden recomendado para CSS de larga vida:

1. `data-store`
2. IDs o clases estructurales documentadas por snippets oficiales
3. clases utilitarias de Bootstrap 4 solo como contexto
4. clases `js-*` solo cuando no haya anchor mejor
5. etiquetas HTML solas solo para reglas tipograficas internas y muy contenidas

Ejemplos buenos:

- `[data-store="product-detail"]`
- `[data-store^="product-item-"]`
- `[data-store^="product-item-name-"]`
- `[data-store^="product-item-price-"]`
- `[data-store^="product-name-"]`
- `[data-store^="product-price-"]`
- `[data-store="filters-nav"]`
- `[data-store="footer"]`

Ejemplos mas fragiles:

- `.row .col .btn`
- `.js-*` sin scope padre
- `div > div > div > h4`

## Capa 5: que cambia entre plantillas y que importa en Morelia

## Estable entre plantillas nativas modernas

- stack Bootstrap 4 + utilities
- uso de `data-store`
- familia de componentes de producto, grid, shipping, payments, header y footer
- presencia de tags HTML basicos similares

## Variable entre plantillas

- disponibilidad de modulos de home
- orden de secciones
- wrappers visuales adicionales
- clases cosmeticas del theme
- algunos layouts de navegacion, filtros y cards

## En Morelia conviene asumir

- home mas rica que Base en cantidad de modulos opcionales
- producto, grilla y listados alineados con familia Rio/Lima/Cali/Uyuni/Toluca/Recife/Baires
- misma disciplina: el anchor confiable es `data-store` y luego los componentes documentados

## Zonas donde una inspeccion del DOM real sigue siendo obligatoria

- variantes estilo boton o color
- bloques de home activados solo por configuracion del comerciante
- componentes privados nuevos o rollout gradual
- contenido HTML libre de descripciones y paginas internas
- tiendas con historial de customizaciones por FTP

## Reglas practicas para editar CSS con precision

### Seguro

- tipografia interna dentro de un scope `data-store`
- espaciado de wrappers documentados
- color y border de cards, labels y botones
- jerarquia tipografica de `h1` a `h6`, `p`, `span`, `small` dentro de un modulo identificado

### Requiere prueba funcional

- `display`, `position`, `overflow` o `height` en product form, shipping, payments y cart
- reordenar flex/grid de formularios
- ocultar mensajes o bloques que el JS actualiza

### Evitar sin evidencia adicional

- atacar solo por etiqueta global como `input`, `button`, `img`, `table`
- asumir que Morelia renderiza siempre todos los modulos que soporta
- depender de wrappers no documentados cuando existe `data-store`

## Conclusiones accionables

- Si el objetivo es controlar el CSS con precision, la unidad correcta no es "cada etiqueta aislada" sino `template + componente + data-store + etiqueta interna`.
- Para Morelia, la mejor referencia oficial sigue siendo Base mas Snipplets mas Puntos de anclaje mas Componentes privados.
- La mayor parte del trabajo de CSS futuro puede apoyarse en esta jerarquia: scope oficial de pantalla, componente documentado, luego tipografia y layout interno.
- Cuando aparezca un bloque nuevo en preview, primero hay que ubicar si corresponde a un `data-store` oficial, a un componente privado o a una capa custom del theme.

## Fuentes oficiales consultadas

- https://docs.tiendanube.com/help/theme-base
- https://docs.tiendanube.com/help/acerca-del-theme-base
- https://docs.tiendanube.com/help/estructura-de-carpetas
- https://docs.tiendanube.com/help/layouts
- https://docs.tiendanube.com/help/templates
- https://docs.tiendanube.com/help/templates-home
- https://docs.tiendanube.com/help/snipplets
- https://docs.tiendanube.com/help/sections
- https://docs.tiendanube.com/help/codigo-objetos
- https://docs.tiendanube.com/help/qu-es-twig
- https://docs.tiendanube.com/help/otras-plantillas-nativas-de-tiendanube
- https://docs.tiendanube.com/help/puntos-de-anclaje-para-aplicaciones
- https://docs.tiendanube.com/help/componentes-privados
- https://docs.tiendanube.com/help/calculador-de-envos
- https://docs.tiendanube.com/help/informacin-de-medios-de-pago-y-cuotas-jq-nuvem
- https://docs.tiendanube.com/help/mensaje-de-descuento-sobre-precio-no-combinable