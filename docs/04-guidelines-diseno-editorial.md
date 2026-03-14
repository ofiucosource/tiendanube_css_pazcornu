# Guidelines de diseno editorial

## Objetivo

Definir una base visual consistente para futuras iteraciones del CSS, tomando como referencia el estado actual del proyecto y la direccion buscada: editorial, sobria, ordenada y con foco en legibilidad y jerarquia.

## Principios rectores

- Silencio visual antes que decoracion.
- La ropa y la fotografia deben dominar por encima de la interfaz.
- La jerarquia debe construirse con espaciado, peso tipografico y contraste, no con efectos.
- Cada bloque debe verse limpio, respirado y facil de escanear.

## Sistema visual

### Paleta

- Base principal: blanco, negro y grises neutros.
- Negro funcional: `#111111` para texto principal, CTAs y titulos.
- Gris texto: `#333333` para descripcion de producto.
- Gris medio: `#444444` a `#666666` para texto secundario y subitems de dropdown.
- Gris placeholder: `#999999` para placeholders del buscador.
- Gris borde funcional: `#c8c8c8` a `#d8d8d8` para bordes de inputs, variantes, paginacion y sort-by.
- Gris suave estructural: `#e0e0e0` a `#ebebeb` para separadores, bordes de header y hover de CTA en grilla.
- Fondos neutros: `#faf9f7` para imagen quickshop, `#f6f3ef` para imagen del textbanner.
- Evitar colores acento salvo necesidad funcional muy puntual.

### Tipografia

- Tono general: editorial, austero, ligero.
- Uso extensivo de uppercase para navegacion, labels, subtitulos y nombres de categoria.
- `letter-spacing` moderado para dar aire sin volver rigido el texto.
- Pesos recomendados:
  - `300` para secundarios y subitems.
  - `400` para navegacion principal, nombres y precios.
  - `600` para encabezados de subcategorias y microjerarquias.

### Bordes y superficies

- Bordes rectos, sin radios visibles salvo requerimiento funcional.
- Sin sombras pesadas ni efectos glossy.
- Superficies blancas o transparentes como base.
- Separadores finos y discretos para ordenar, no para llamar la atencion.

## Navbar y navegacion

### Header

- Debe sentirse liviano y estable.
- El logo necesita aire vertical y no debe competir con la navegacion.
- Los iconos de utilidad deben mantenerse sobrios, con hover por opacidad o contraste simple.

### Menu principal desktop

- Texto en uppercase con tracking fino.
- Hover sin fondos invasivos ni cambios bruscos.
- La navegacion debe verse premium, no promocional.

### Dropdowns y submenus

- Deben comportarse como paneles editoriales, no como menus tecnicos densos.
- Fondo blanco, borde superior sutil y sombra muy contenida.
- Columnas con ancho consistente para evitar superposiciones.
- Encabezados de subcategoria claramente diferenciados de sus items hijos.
- Encabezados:
  - peso `600`
  - color `#111111`
  - separacion inferior clara
- Subitems:
  - peso `300`
  - color gris medio
  - espaciado corto y prolijo

### Categorias y subcategorias

- Las paginas de listado deben verse como extension natural del home, no como otro theme.
- Cards, precios y CTAs deben compartir exactamente el mismo lenguaje visual de la home cuando el markup lo permita.
- Navegacion lateral, filtros y paginacion deben sentirse silenciosos y funcionales, nunca mas protagonistas que la grilla.
- Si una categoria usa un wrapper distinto, primero se valida en preview y luego se suma como scope compatibile, en lugar de asumir markup generico.

## Producto

### Detalle de producto

- El titulo debe verse presente, no pesado.
- El precio debe ser claro y directo.
- Breadcrumbs y mensajes secundarios deben permanecer silenciosos.
- Variantes y cantidades deben sentirse limpias, funcionales y austeras.
- El CTA principal puede ser firme, pero sin look promocional agresivo.

### Grilla de productos

- La imagen es la protagonista.
- Nombre y precio deben acompañar, no competir.
- Hover de imagen suave y controlado.
- El CTA debe ser corto, fino y visualmente subordinado a la foto.

## Comportamientos interactivos

- Preferir transiciones cortas y sobrias.
- Evitar animaciones elásticas, rebotes o escalas exageradas.
- Los hovers deben comunicar precision y no espectacularidad.

## Criterios para nuevos cambios

- Si un ajuste agrega ruido visual, probablemente no va en esta direccion.
- Si un ajuste mejora lectura, orden o aire, probablemente si.
- Priorizar hooks estables como `data-store` cuando sea posible.
- Evitar depender de clases `js-*` salvo que no exista alternativa segura.
- Antes de subir contraste o peso, probar primero con espaciado y jerarquia estructural.
- En listados, reutilizar primero los scopes ya validados en preview antes de abrir nuevos fallbacks.

## Regla anti-alucinacion para futuras iteraciones

- No asumir que una pagina de categoria usa el mismo wrapper que home solo por similitud visual.
- No abrir un selector nuevo para listados sin comprobar antes si ya existe un scope validado en `02-mapa-selectores-theme-actual.md`.
- Si un bloque toca cards, filtros o paginacion, se prueba primero sobre hooks de item y wrappers ya confirmados en preview.
- Cuando haya duda entre `data-store` y una clase `js-*`, se elige `data-store` primero.

## Anti-patrones

- Sombras grandes.
- Gradientes fuertes.
- Colores acento arbitrarios.
- Tipografia decorativa fuera de sistema.
- Menus comprimidos o con columnas demasiado angostas.
- CTAs que visualmente gritan mas que el producto.
- CSS nuevo basado en wrappers no verificados cuando ya existen scopes validados.

## Resumen operativo

La tienda debe sentirse limpia, refinada y coherente. La referencia no es una estetica llamativa, sino una interfaz silenciosa que deja protagonismo al contenido y ordena la navegacion con jerarquia clara.