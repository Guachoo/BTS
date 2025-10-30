# BTS - Deploy en Vercel

Este proyecto es una página estática (`index.html`) que muestra gráficos con Chart.js, exporta a PDF con html2canvas + jsPDF y mantiene datos en `localStorage`.

A continuación tienes instrucciones para desplegar en Vercel tanto desde la CLI como conectando un repositorio Git (GitHub/GitLab/Bitbucket).

---

## Opción A — Rápido: desplegar desde tu máquina con la CLI (PowerShell)

1. Instala Node.js (si no lo tienes). Recomendado: v18+.
2. Abre PowerShell en la carpeta del proyecto (donde está `index.html`).
3. Instala la CLI de Vercel si no la tienes:

```powershell
npm install -g vercel
```

4. Inicia sesión (sigue el prompt):

```powershell
vercel login
```

5. Despliega por primera vez (esto crea el proyecto en tu cuenta):

```powershell
vercel --prod
```

- Durante el primer deploy la CLI te preguntará por nombre del proyecto y opciones; acepta o elige según prefieras.
- Para despliegues siguientes, ejecutar `vercel --prod` desde el mismo directorio actualizará el sitio.

6. Al terminar la CLI imprimirá la URL pública (ej: `https://your-project.vercel.app`).

Notas:
- Si quieres desplegar sin publicar inmediatamente, usa `vercel` (sin `--prod`) para un preview.

---

## Opción B — Conectar un repositorio Git (recommended para CI)

1. Crea un repositorio (GitHub/GitLab/Bitbucket) y sube tu proyecto (commit + push).
2. En https://vercel.com, crea un nuevo proyecto y elige "Importar proyecto" desde Git.
3. Selecciona el repo y configura (usualmente no necesitas cambiar nada para un sitio estático).
4. Vercel hará deploy automáticamente cada vez que pushes al branch configurado (ej: `main`).

---

## Archivos incluidos para Vercel

- `vercel.json` — configuración mínima para servir `index.html` y habilitar fallback (SPA).

---

## Recomendaciones

- Si usas recursos externos (CDN), Vercel los sirve normalmente; si necesitas CORS en html2canvas, asegúrate que las imágenes permitan `Access-Control-Allow-Origin`.
- Si el PDF pesa mucho, reduce la `scale` usada en la función de exportación (`exportChartsAndTableToPdf`) en `index.html`.

---

Si quieres, puedo:
- Crear el repo remoto (necesitaré acceso/credenciales, lo cual no puedo hacer por ti) o guiarte paso a paso.
- Ajustar la configuración (`vercel.json`) para otros comportamientos.
- Preparar un `package.json` y script de deploy si prefieres automatizar con GitHub Actions.

¿Con cuál opción quieres que te guíe (CLI ahora / conectar repo / crear GitHub Actions)?
