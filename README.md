# Video por código — skill para Claude Code

Por **Jorge Torres** · Licencia MIT

Una skill que le enseña a Claude Code a hacer **videos animados sin grabar nada**: tú le pasas
un tema, un texto, una propuesta o unas cifras, y él escribe el guion, le pone voz en off,
anima cada escena por código y te entrega un MP4 listo para LinkedIn, Instagram o una
presentación.

## Qué le puedes pedir

> «Hazme un video de 45 segundos sobre los resultados del trimestre, con estas cifras: …»
> «Convierte esta propuesta en un video para mandarle al cliente.»
> «Un reel vertical con estos tres datos.»
> «Un video explicativo de cómo funciona nuestro servicio, con voz.»

## Qué hace

1. **Escribe el guion** (o usa el tuyo palabra por palabra) y te lo muestra antes de seguir.
2. **Le pone voz en off en español** con inteligencia artificial (OpenAI). Opcional.
3. **Anima cada escena por código**: textos que se arman, cifras que cuentan hasta su valor,
   barras que crecen. Cada animación aparece **justo cuando la voz dice la palabra**.
4. **Exporta MP4** en 1080p, horizontal (16:9) o vertical (9:16), con la voz normalizada al
   volumen estándar de redes. Si tienes una música con derechos, la mezcla por debajo de la voz.
5. **Se revisa a sí mismo**: antes de entregarte nada, saca una hoja con 30 cuadros del video,
   la mira y corrige lo que esté cortado, ilegible o fuera de tiempo.
6. **Te entrega dos versiones distintas** para que escojas, y tus comentarios se aplican a la
   que elegiste.

**Lo que no hace:** editar videos grabados (cortar silencios o muletillas), avatares ni clonar
voces. Nunca inventa cifras: los datos salen solo del material que le das.

## Instalación (una sola vez, ~10 minutos)

### 1. Descargar

Botón verde **Code → Download ZIP** arriba en esta página, y descomprimir.

### 2. Copiar la skill

Copia la carpeta `video-por-codigo` dentro de la carpeta de skills de Claude Code:

**macOS / Linux**
```bash
mkdir -p ~/.claude/skills
cp -r video-por-codigo ~/.claude/skills/
```

**Windows (PowerShell)**
```powershell
mkdir "$env:USERPROFILE\.claude\skills" -Force
Copy-Item video-por-codigo "$env:USERPROFILE\.claude\skills\" -Recurse
```

Debe quedar `~/.claude/skills/video-por-codigo/SKILL.md`.

### 3. Programas que necesita

| Qué | macOS | Windows |
|---|---|---|
| Python 3.9+ | ya viene, o https://www.python.org/downloads/ | https://www.python.org/downloads/ (marcar «Add to PATH») |
| ffmpeg | `brew install ffmpeg` | `winget install --id Gyan.FFmpeg` |
| Librerías | `python3 -m pip install requests playwright` | `py -m pip install requests playwright` |
| Navegador para grabar | `python3 -m playwright install chromium` | `py -m playwright install chromium` |

> ¿No te quieres pelear con la terminal? Abre Claude Code y dile:
> **«Instala lo que necesita la skill video-por-codigo»**. Él corre el chequeo y lo instala.

### 4. Tu API key de OpenAI (solo para la voz)

Crea el archivo `~/.claude/.env` (en Windows: `C:\Users\TU_USUARIO\.claude\.env`) con esta línea:

```
OPENAI_API_KEY=sk-...
```

La voz cuesta **unos centavos de dólar por video**. Sin key, los videos salen con texto y
música, sin voz.

### 5. Comprobar

Reinicia Claude Code y corre:

```bash
python3 ~/.claude/skills/video-por-codigo/scripts/revisar_entorno.py
```

Si todo sale `OK`, ya está. Pídele tu primer video.

## Cuánto tarda

Un video de 45–60 segundos toma entre 20 y 40 minutos de trabajo de Claude (guion, voz, dos
versiones y dos o tres rondas de revisión). En la prueba, cada render de 50 segundos tardó 3–4
minutos con las dos versiones en paralelo, y cada ronda de corrección unos 6–8 minutos.

## Cómo está hecha

```
video-por-codigo/
├── SKILL.md              el flujo que sigue Claude
├── references/
│   ├── encargo.md        cómo se le pide la escena al modelo para que no salga genérica
│   ├── oficio.md         ritmo, sincronía, tipografía, cifras y señales de «hecho por IA»
│   └── voz.md            cómo se escribe un guion para oír (y cómo se arregla la pronunciación)
├── plantilla/escena.html el contrato técnico de cada escena
└── scripts/
    ├── revisar_entorno.py  chequea lo instalado y dice cómo arreglar lo que falte
    ├── voz.py              guion → voz + tiempo exacto de cada palabra
    ├── render.py           escena HTML → MP4 cuadro por cuadro, con audio
    └── hoja.py             hoja de 30 cuadros para revisar el video de un vistazo
```

La idea de fondo: un modelo rinde mejor cuando se le da **criterio** (qué hace bueno a un video)
que cuando se le da una plantilla de diseño. Por eso la skill no trae estilos fijos: trae el
oficio, la forma de pedirle las cosas y la obligación de mirarse antes de entregar.
