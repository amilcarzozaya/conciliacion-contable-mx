# conciliacion-contable-mx

Skill para conciliar el estado de cuenta bancario contra el auxiliar contable de una empresa mexicana y vincular los movimientos con CFDI. Funciona como copiloto de auditoría para un contador público: encuentra coincidencias, aísla diferencias, cuantifica su impacto y deja evidencia trazable.

No sustituye al contador. Propone; el contador aprueba.

## Qué hace

- Inventaría los archivos, valida periodo, moneda y saldos, y confirma la convención de cargos/abonos y debe/haber antes de comparar.
- Normaliza fechas, importes y referencias sin perder los valores originales.
- Empareja por niveles: exactos, probables y agrupados (uno a muchos y muchos a uno). Ningún movimiento se usa dos veces.
- Detecta duplicados, diferencias de importe, posibles registros omitidos y partidas en tránsito.
- Revisa vínculos con CFDI (UUID, método de pago PUE/PPD, complementos de pago) sin dar por pagada una factura solo porque existe.
- Recalcula saldos y entrega una prueba matemática de conciliación.
- Sugiere pólizas solo cuando hay sustento, y verifica que cada una cuadre (Debe = Haber).

## Qué entrega

1. Resumen ejecutivo con importes y conteos.
2. Matriz de conciliación con trazabilidad (`archivo|hoja|fila`).
3. Tabla de excepciones con prioridad, evidencia y acción.
4. Prueba matemática de saldos.
5. Borradores de pólizas sugeridas.
6. Lista de cuestiones que debe aprobar o investigar el contador.

## Qué no hace

- No consulta el SAT. Vigencia, cancelación y RFC quedan como "no verificados".
- No determina impuestos ni ajustes definitivos.
- No modifica los archivos originales.
- No declara "conciliación total" mientras haya diferencias sin resolver.
- Si falta un dato indispensable, se detiene y dice cuál.

## Qué necesita

- Estado de cuenta bancario del periodo (Excel o CSV).
- Auxiliar contable de la cuenta de bancos (por ejemplo, exportado de Aspel COI).
- Opcional: CFDI en XML (incluidos complementos de pago) y catálogo de cuentas.

## Instalación

**Claude Code**

```bash
git clone https://github.com/amilcarzozaya/conciliacion-contable-mx ~/.claude/skills/conciliacion-contable-mx
```

**Claude.ai**

Comprime la carpeta `conciliacion-contable-mx` en un `.zip` y súbela en la sección de Skills.

## Uso

Adjunta los archivos y escribe algo como:

> Concilia el estado de cuenta de septiembre de 2026 contra el auxiliar contable y vincula los movimientos con los CFDI. Los datos son de un caso educativo ficticio.

La skill empieza revisando los archivos y reportando cualquier dato faltante. Después hace la conciliación.

## Datos reales

No subas a este repositorio estados de cuenta, auxiliares ni CFDI reales. El `.gitignore` bloquea por defecto `.xlsx`, `.xls`, `.csv`, `.xml` y `.pdf` para evitar accidentes. Los ejemplos que se agreguen deben ser siempre datos simulados.

## Estado

Versión 0.1.0, borrador. Aún no se prueba con un lote completo. Pendiente: un conjunto sintético con errores sembrados (duplicados, transposición de dígitos, PPD sin complemento) para validar los resultados.

## Aviso

Herramienta de apoyo. El contador responsable valida cada resultado antes de usarlo. Nada de lo que produce constituye asesoría fiscal o legal.

## Licencia

MIT. Ver [LICENSE](LICENSE).

## Autor

**Amilcar Zozaya** es autor y conferencista. Creó Campus MANGO y el Método MANGO.

Más en [campusmango.com](https://campusmango.com).
