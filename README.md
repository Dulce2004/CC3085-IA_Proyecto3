# Proyecto 3 — Inteligencia Artificial (CC3085)

## VeritasAI: Motor de Inferencia Legal con Lógica de Horn

### Integrantes

| Nombre               | Carnet  |
|----------------------|---------|
| Dulce Ambrosio       | 231143  |
| Daniel Chet          | 231177  |
| Gadiel Ocaña         | 231270  |
| Melisa Mendizabal    | 23778   |
| Renato Rojas         | 23813   |
| Micaela Pop          | 18960   |

---

## Descripción

**VeritasAI** es una startup guatemalteca que automatiza la auditoría legal de contratos. En lugar de que un abogado revise manualmente cientos de reglas, el sistema las procesa lógicamente en segundos mediante un motor de inferencia basado en lógica proposicional.

---

## Contenido del Notebook

### Sección 1 — Cláusulas de Horn: La Base de Conocimiento

Se define una **Knowledge Base (KB)** con 8 cláusulas de Horn en el formato `(premisas, conclusión)`. Cada regla tiene exactamente una conclusión positiva, lo que garantiza eficiencia lineal en el motor.

Ejemplos de reglas:
- `contrato_vencido ∧ monto_alto → revision_legal`
- `firma_invalida → bloquear_contrato`
- `proveedor_sin_licencia → contrato_invalido`

### Sección 2 — Motor de Inferencia Interactivo (Modus Ponens)

Implementación de **Forward Chaining** con Modus Ponens. El usuario puede seleccionar condiciones del contrato mediante checkboxes y el sistema deduce automáticamente las acciones legales correspondientes.

**Lógica:** Si `P → Q` y `P` es verdad, entonces `Q` es verdad. El motor aplica esto iterativamente hasta que no se puedan inferir nuevos hechos.

### Sección 3 — Visualización de Modus Ponens

Diagramas paso a paso de tres ejemplos de aplicación del Modus Ponens, incluyendo un caso de encadenamiento donde una conclusión sirve como premisa para la siguiente regla.

### Sección 4 — Conversión a Forma Normal Conjuntiva (CNF)

Transformación algebraica de las reglas usando **SymPy**:
1. Eliminación de la implicación (`P → Q ≡ ¬P ∨ Q`)
2. Aplicación de De Morgan
3. Distribución hasta obtener la CNF

La CNF es requerida por el algoritmo de resolución para detectar contradicciones de forma uniforme y automática.

### Sección 5 — Grafo del Motor de Inferencia

Visualización con **NetworkX** del flujo lógico completo: desde los datos del contrato (hechos base) hasta las acciones legales finales, pasando por conclusiones intermedias.

### Sección 6 — Completitud

Demostración de que el motor deriva **todas** las conclusiones verdaderas derivables de las reglas, incluyendo cadenas largas de inferencia. Sin completitud, un contrato que debía escalarse a la junta directiva podría clasificarse erróneamente como válido.

### Sección 7 — Resumen

Diagrama que resume los 4 pilares del motor de VeritasAI:
1. **Cláusulas de Horn** — almacenan reglas con una sola conclusión
2. **CNF** — estandariza fórmulas para resolución
3. **Modus Ponens** — dispara inferencias paso a paso
4. **Completitud** — garantiza que ninguna conclusión se pierda

---

## Tecnologías Utilizadas

- **Python 3**
- `sympy` — conversión a CNF y manipulación simbólica
- `networkx` — grafos de inferencia
- `matplotlib` — visualizaciones
- `ipywidgets` — interfaz interactiva
- `pandas` — tablas de la KB y pasos de inferencia

---

## Ejecución

1. Abrir `Proyecto3.ipynb` en Jupyter Notebook o VS Code.
2. Ejecutar todas las celdas en orden.
3. En la **Sección 2**, seleccionar las condiciones del contrato y presionar **Analizar Contrato** para ver las inferencias en tiempo real.
