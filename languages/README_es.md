# LinkClean - Limpiador de enlaces

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Antes de compartir, quita el lastre de seguimiento. Pega una URL y LinkClean enumera cada parámetro eliminado, desarma redirecciones y páginas AMP, y te devuelve un enlace limpio. Todo ocurre en tu dispositivo: ningún enlace sale del navegador.

## Funciones

- **Un pegado, un enlace limpio** — pega una URL o toma la pestaña en la que estás.
- **Nada desaparece en silencio** — cada parámetro eliminado aparece por su nombre, con el valor que habría recibido el sitio.
- **Copia como URL o como Markdown** — el Markdown se construye con el título real: `[título](url)`.
- **Modo por lotes** — acepta una lista de URL, pero también un párrafo, un correo o un chat. Solo se reescriben los enlaces; el texto de alrededor queda intacto.
- **Los parámetros funcionales se quedan** — solo se eliminan 58 nombres de seguimiento conocidos y 11 familias de prefijos (`utm_`, `ga_`, `mtm_`, `piwik_`, `_hs` y otras).
- **Pro: desarmar redirecciones** — Google, YouTube, Facebook, Reddit, DuckDuckGo, LinkedIn, Zhihu, Douban, Jianshu, SSPAI, VK, Slack, Outlook Safe Links, Skimlinks, Tumblr, Medium, Pocket, además de Bing, Weibo, Proofpoint y la forma genérica `/redirect?url=` — en local, recursivo, hasta tres saltos.
- **Pro: resolución AMP** — `cdn.ampproject.org/c/s/`, `google.com/amp/s/` y un `/amp` final vuelven a la página canónica.
- **Pro: reglas por sitio** — `amazon.com` conserva `th` y `psc` mientras se quita todo lo demás. Gana el dominio más específico y los subdominios lo heredan. Pulsa cualquier parámetro eliminado y quedará conservado en ese sitio para siempre.
- **Pro: historial y contadores** — busca por enlace, título o dominio, copia el enlace original, exporta JSON; además contadores de enlaces limpiados y parámetros eliminados.

## Gratis vs Pro

| | Gratis | Pro |
|---|---|---|
| Limpieza de un enlace (lista integrada completa) | ✅ | ✅ |
| Copia Markdown / portapapeles / interruptor de fragmentos | ✅ | ✅ |
| Copia automática tras limpiar | ✅ | ✅ |
| Tamaño del lote | 10 enlaces | ilimitado |
| Exportación TXT | ✅ | ✅ |
| Exportación CSV / JSON | — | ✅ |
| Párrafos con varios enlaces | hasta 10 | ✅ |
| Desarmar redirecciones y AMP | solo aviso | ✅ |
| Reglas por sitio + conservar en un clic | — | ✅ |
| Historial | 10 entradas | 100, con búsqueda y enlace original |
| Paquetes de reglas (importar/exportar) | — | ✅ |
| Desglose de sitios más frecuentes | — | ✅ |

Una clave activa dos navegadores; al quitarla, la plaza vuelve a quedar libre. Comprobación cada dos horas aproximadamente, sin conexión vale la licencia en caché; si falla, no se bloquea nada.

## Cómo se usa

1. Pulsa el icono de LinkClean. Si la página actual lleva parámetros de seguimiento, el campo ya viene relleno.
2. Pulsa «Limpiar enlace». El resultado muestra la URL limpia, cada parámetro eliminado como etiqueta y, con licencia y si había redirección, la cadena resuelta.
3. Copia el enlace, cópialo como Markdown, ábrelo o pásalo al modo por lotes.
4. ¿Un parámetro no debía desaparecer? Púlsalo en el resultado y quedará en la lista de conservados de ese sitio.

## Privacidad

- Los enlaces no salen del navegador. Cada regla es una operación local con cadenas; **no se descarga ninguna redirección para averiguar su destino**.
- Sin analíticas, sin telemetría, sin identificadores publicitarios, sin píxeles de seguimiento.
- El historial, los ajustes y los contadores viven en `chrome.storage.local` y pueden borrarse en cualquier momento.
- La única petición de red es la comprobación de licencia: clave, identificador de instalación aleatorio, id del plugin y metadatos básicos del navegador.
- El portapapeles solo se lee al pulsar Pegar, y solo se escribe al copiar o con la copia automática activada.

## Permisos

| Permiso | Para qué |
|---|---|
| `storage` | Guardar ajustes, reglas propias, historial y estado de licencia en local |
| `activeTab` | Leer la URL de la página actual, solo después de pulsar el icono |
| `clipboardWrite` | Escribir el enlace limpio al copiar o con la copia automática |
| `clipboardRead` | Leer el portapapeles solo al pulsar Pegar, nunca en segundo plano |
| `https://api.annmax1983.com/*` | Solo activación y comprobación de licencia; nunca un enlace |

Sin content script, sin acceso a `<all_urls>`, sin permiso `tabs` y sin permiso `downloads`: LinkClean no puede ver el texto de ninguna página.

## Navegadores compatibles

Chrome y Edge (Manifest V3, Chrome 116+). La versión para Firefox está en preparación.

## Desarrollo

```bash
npm install        # única dependencia de desarrollo: terser
npm run locales    # genera los seis _locales desde tools/make-locales.js
npm run icons      # genera los iconos
npm test           # node --test: limpieza, redirecciones, reglas por sitio, i18n, cableado del panel
npm run build      # minifica y empaqueta → publish/linkclean-v{version}.zip
node tools/shoot.js  # capturas 1280×800 y promo en Chrome real
```

> Este repositorio es solo para presentar el proyecto; el código completo no se publica. Instala LinkClean desde las tiendas oficiales de navegadores.

## Enlaces

- Sitio web: https://annmax1983.com
- Página de la extensión: https://annmax1983.com/extensions/linkclean
- Licencia y precio: https://annmax1983.com/checkout?plugin=linkclean
