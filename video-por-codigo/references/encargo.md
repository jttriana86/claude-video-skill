# Cómo se le escribe el encargo al agente que hace la escena

Lo que se le dice al modelo pesa más de lo que parece. Estas reglas salen de probar muchas
veces la misma pieza cambiando solo el encargo.

## Lo que pasa según cómo se le pide

| Si le das… | Pasa esto | Entonces |
|---|---|---|
| Una imagen concreta («como un cohete», «estilo constelación») | Se vuelve el tema: dibuja cohetes | Dile qué debe **sentir** quien lo ve, nunca qué dibujar |
| Un freno solo («menos efectos») | Se va al otro extremo: queda estático | Cada «no» va con su «en su lugar», y con rango |
| Un mínimo suelto («al menos 40 cortes») | Se pasa y marea | Rangos de dos lados: «entre 8 y 20» |
| La misma palabra muchas veces | Se vuelve el centro del video | Cada idea una vez, en proporción a su importancia |
| Tono cauteloso («educativo», «sencillo», «una idea a la vez») | Baja el techo: sale lento y plano | La claridad se pide como oficio medible, no como tono |
| Ambición («que impresione a un experto y a un niño») | Sube el techo | Va al inicio del encargo |
| Referencias antes de idear | Las copia | Si hay referencia, se mira al final, para comparar |

## Plantilla del encargo (adaptar, no recortar)

> Eres el mejor director de motion graphics con el que he trabajado. Quiero una pieza que deje
> sin palabras a quien la vea: a un experto en el tema, a alguien que nunca ha oído de él y a un
> niño. Estoy harto de los videos corporativos promedio que se ven todos iguales.
>
> **Material:** [ruta al guion / documento / cifras]. Estúdialo tú; de ahí sale todo el contenido.
> No inventes cifras ni nombres.
>
> **Lo que debe sentir quien lo ve:** [una línea abstracta, sin imágenes: «confianza en que esto
> ya funciona», «urgencia», «orgullo»].
>
> **La voz ya existe:** `window.VOZ` trae cada palabra con su segundo. Que lo importante aparezca
> justo cuando se dice.
>
> **Antes de programar**, escribe en `tratamiento.md`: 10 ideas de cómo contarlo, tacha las
> obvias, elige una y di por qué; la paleta (pocos colores, un acento que se gana su momento),
> las tipografías y qué papel tiene cada una, y la lista de lo que esta pieza no va a tener.
>
> **Vetos** (cada uno con su alternativa):
> - Nada de íconos genéricos ni de cajitas con borde de color para destacar una nota; en su
>   lugar, el dato grande y la frase clave resaltada con el color de acento.
> - Nada de un punto de color delante de un rótulo; en su lugar, el rótulo solo, bien espaciado.
> - Nada de texto que solo aparece con un fundido; en su lugar, texto que entra con intención
>   (se escribe, se arma, empuja algo, crece desde el dato).
>
> **Ritmo:** entre 10 y 25 cambios de plano por minuto; lo que hay que recordar se queda quieto
> al menos un segundo.
>
> El texto en pantalla sale del material, no del guion de la voz (el guion puede traer palabras
> escritas como se pronuncian).
>
> Lee `<skill>/references/oficio.md` antes de empezar. Copia `<skill>/plantilla/escena.html` a tu
> carpeta y respeta su contrato. Renderiza, abre la hoja de cuadros y **mírala**, corrige y repite
> hasta que no puedas nombrar algo que lo mejore. No me des un plan: hazlo. Tómate el tiempo que
> necesites.
>
> Comandos:
> ```
> python3 <skill>/scripts/render.py [carpeta]/escena.html --audio [video]/voz.wav --workers 2 [--vertical] [--desde 12 --hasta 16]
> python3 <skill>/scripts/hoja.py [carpeta]/escena.mp4
> ```
>
> **Entrega:** `escena.html` y `escena.mp4` en [carpeta], [1920×1080 o 1080×1920]. Al terminar,
> dime cuántas rondas hiciste y qué corregiste en cada una.

Para la versión B, el mismo encargo en otra carpeta **con otra línea de sentimiento** (si A es
«alivio», B puede ser «urgencia» u «orgullo»): con el encargo idéntico las dos salen con la misma
estructura y solo cambia la estética. Cambia solo esa línea; lo demás igual.

## Lo que NO va en el encargo

Lista de escenas, paleta impuesta (salvo marca del cliente), herramientas obligatorias, ejemplos de
otros videos u opiniones tuyas sobre el contenido. Cada una de esas cosas lo acerca a lo que ya
imaginaste y le quita lo que él podía proponer.

## Después de que el usuario elige

- El comentario del usuario se aplica a **esa** pieza, con el mismo agente si es posible.
- Un comentario no se convierte en regla para todos los videos a la primera: solo si se repite
  o el usuario lo pide así. Entonces se añade a `oficio.md`, con su «en su lugar».
