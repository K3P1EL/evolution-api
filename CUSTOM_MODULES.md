# Custom modules

Código propietario de Danochiss / Matrix Perfecta.

**REGLA:** Todo lo que vaya aquí NO se toca al hacer `git merge upstream/main`. Mantén los cambios al core de Evolution al mínimo absoluto (idealmente 1 línea por hook).

## Archivos

- `buttons-handler.ts` — Lógica custom de botones (estabiliza el envío, agrega sintaxis propia)
- `matrix-perfecta.ts` — Puente con Cloudflare Worker para agrupar ráfagas 15s (futuro)

## Cómo traer features de Evolution oficial

```bash
git fetch upstream
git log upstream/main --oneline  # ver qué hay nuevo
git cherry-pick COMMIT_HASH      # traer solo lo que queremos
```

Si cherry-pick tiene conflicto en `src/custom/*`, es un bug — upstream no debería tocar esta carpeta.

## Cómo subir a producción

```bash
git add .
git commit -m "feat(custom): description"
git push origin custom
```

Easypanel detecta el push (cuando configuremos Git deploy) y redeploya automáticamente.
