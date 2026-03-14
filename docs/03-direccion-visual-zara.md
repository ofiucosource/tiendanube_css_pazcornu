# Direccion visual inspirada en Zara, adaptada al proyecto actual

## Objetivo

Definir una guia visual para futuras iteraciones de CSS inspirada en la logica editorial y minimalista de Zara, pero sin copiar su identidad ni romper los lineamientos ya presentes en el proyecto.

## Punto de partida actual

El CSS existente ya tiene varios rasgos compatibles con esa direccion:

- paleta neutra blanco / negro / grises
- mucho uso de mayusculas
- bordes rectos
- peso visual sobrio
- hover discretos
- tipografia liviana

La oportunidad no es cambiar de universo visual, sino depurarlo.

## Que tomar de la referencia Zara

### 1. Silencio visual

- menos ruido de color
- menos jerarquias secundarias compitiendo con el nombre del producto
- mas aire alrededor del contenido

### 2. Jerarquia editorial

- titulo de producto con presencia pero sin exceso de peso
- precio claro, no gritante
- labels y subtitulos en mayusculas pequeñas y muy ordenadas

### 3. Controles austeros

- botones de borde recto
- estados hover por inversion simple o cambio de relleno muy controlado
- variantes como piezas limpias, casi tipograficas

### 4. Imagen como protagonista

- cards con imagen limpia y texto subordinado
- zoom hover minimo
- evitar sombras, gradientes fuertes o efectos decorativos innecesarios

## Que NO conviene hacer

- no meter serif decorativa si el sitio no la sostiene completo
- no sumar sombras pesadas
- no usar animaciones grandes o elasticos
- no convertir todo a gris claro porque se pierde contraste de compra
- no copiar layouts de Zara uno a uno

## Traduccion concreta al proyecto actual

## Detalle de producto

Direccion sugerida:

- titulo mas respirado que pesado
- precio con contraste limpio y sin demasiados adornos
- breadcrumbs muy discretos
- variantes con mas aire horizontal y menos apariencia de boton tradicional
- CTA principal contundente, casi editorial, no promocional

Lo que ya funciona en el CSS actual:

- `text-transform: uppercase`
- `letter-spacing` moderado
- CTA con borde negro y hover invertido
- descripcion sobria

Lo que podria ajustarse en futuras rondas:

- separar un poco mas precio, cuotas y shipping para que no queden en bloque compacto
- revisar si la descripcion italic aporta o si conviene reservar italic solo a piezas puntuales
- bajar un poco el peso visual de mensajes secundarios de promo/envio

## Home / grilla

Direccion sugerida:

- card muy limpia
- nombre con buen tracking pero sin verse rigido
- precio mas silencioso que la imagen
- boton corto, recto y discreto

Lo que ya funciona:

- imagen con zoom suave
- nombre en uppercase delgado
- boton de borde fino
- paleta monocromatica

Lo que podria refinarse:

- dar un poco mas de aire entre nombre, precio y CTA
- revisar si el hover gris del boton debe ser mas claro o si conviene inversion blanco/negro segun tono de marca
- asegurar que el CTA no domine mas que la fotografia

## Sistema de color recomendado

Mantener un sistema extremadamente corto:

- negro principal: `#111111`
- gris texto: `#333333`
- gris secundario: `#444444`
- gris borde: `#c8c8c8`
- fondo: `#ffffff`
- hover suave: `#e0e0e0` a `#e6e6e6` segun contexto (grid CTA vs separadores)

Idea central:

- un solo color de acento fuerte no es necesario por ahora
- si aparece un acento, debe ser muy medido y consistente

## Tipografia y tono

Sin cambiar aun la familia tipografica real del storefront, el tono debe ser:

- ligero
- editorial
- seco
- preciso

Parametros utiles para conservar ese tono:

- `font-weight: 300` a `400`
- `letter-spacing` entre `0.04em` y `0.14em` segun jerarquia
- uppercase reservado para titulos cortos, labels y CTA
- textos largos con menos tracking y mejor interlineado

## Motion

Usar movimiento minimo:

- hover de imagen: scale entre `1.02` y `1.04`
- botones: transiciones de `0.2s` a `0.25s`
- sin bounce
- sin blur animado
- sin overlays pesados

## Checklist antes de aprobar una nueva iteracion visual

- la imagen sigue siendo protagonista
- el nombre del producto se lee rapido
- el precio sigue siendo obvio
- el CTA es claro, pero no agresivo
- variantes, cuotas y envio no compiten entre si
- en mobile el ritmo sigue limpio y no se apelmaza

## Propuesta de criterio para siguientes cambios

Prioridad 1:

- ritmo vertical y aire
- consistencia de mayusculas
- refinamiento de CTA

Prioridad 2:

- armonizar estados hover
- limpiar mensajes secundarios
- uniformar bordes y pesos visuales

Prioridad 3:

- revisar microdetalles de variantes y cantidad
- ajustar mobile para que conserve el tono editorial

## Conclusiones

- El proyecto ya esta cerca de una linea editorial sobria compatible con la referencia buscada.
- La mejor evolucion no pasa por agregar recursos visuales, sino por editar mejor el espacio, la jerarquia y el contraste.
- Si avanzamos en CSS, lo mas consistente sera profundizar minimalismo, aire y precision, no complejidad.