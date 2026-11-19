# Módulo B — Conjunto de contraseñas de prueba

**Proyecto:** Hacking Ético — Robo de credenciales con acceso físico y movimiento lateral **Responsable:** Integrante 2 (Módulo B — Cracking de contraseñas offline) **Propósito:** lista de consenso para que Módulo A cree estas cuentas en la VM víctima Windows y la VM víctima Linux del laboratorio oficial del equipo.

---

## Criterios de diseño

- 6 cuentas de prueba, repartidas en 3 niveles de fortaleza (débil, media, fuerte).
- 3 contraseñas quedan **reutilizadas intencionadamente** entre Windows y Linux, una por cada nivel de fortaleza.
- Ninguna contraseña real de nadie del equipo. Todas inventadas para el ejercicio.
- Mismo juego de cuentas se crea en **ambos sistemas operativos** (Windows y Linux), salvo que el equipo decida lo contrario.

---

## Tabla de cuentas de prueba

| # | Usuario | Contraseña | Categoría | Longitud | Composición | ¿Reutilizada en ambos SO? |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | `test_weak1` | `123456` | Débil | 6 | Solo dígitos | No |
| 2 | `test_weak4` | `admin2024` | Débil | 9 | Minúsculas + dígitos (predecible) | **Sí** |
| 3 | `test_med1` | `Madrid2024!` | Media | 11 | Mayús + minús + dígito + símbolo, predecible | No |
| 4 | `test_med4` | `Verano2024$` | Media | 11 | Mismo patrón que #3, mismo "estilo" | **Sí** |
| 5 | `test_strong1` | `xK9#mQ2$vL8p` | Fuerte | 12 | Aleatoria, todos los tipos de carácter | No |
| 6 | `test_strong4` | `correct-horse-battery-42` | Fuerte | 24 | Misma que #5, reutilización incluso en fuertes | **Sí** |

---

## Qué mide cada grupo

- **Débiles (#1–2):** se espera caída casi inmediata con diccionario (rockyou) — sirven de referencia de tiempo mínimo.
- **Medias (#3–4):** mezclan tipos de carácter pero siguen patrones humanos predecibles — es donde debería notarse la diferencia entre diccionario simple y diccionario + reglas.
- **Fuertes (#5–6):** se espera que resistan diccionario y diccionario + reglas; candidatas a no caer ni con fuerza bruta en tiempo razonable — ese "no crackeada" es también un dato válido para la tabla final.
- **Reutilizadas (#2, #4, #6):** mismo usuario/contraseña creado en Windows y en Linux, para comparar el tiempo de crackeo de la misma contraseña en ambos sistemas.
