# Casos de Prueba — SauceDemo

## Convenciones

- **ID:** `TC-[MOD]-[NNN]`.
- **Prioridad:** Alta / Media / Baja.
- **Estado:** Draft (Sin ejecutar) / Passed / Failed / Blocked / Skipped.
- **Nivel:** E2E-UI (todos los casos se ejecutan desde la interfaz).
- **Tipo:** Functional / Smoke / Exploratory

---

### TC-LGN-001 — Login exitoso con standard_user

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Login |
| **Requisito asociado** | REQ-001 |
| **Prioridad** | Alta |
| **Nivel** | E2E-UI |
| **Tipo** | Functional / Smoke |
| **¿Automatizable?** | Sí |
| **Automatización** | [`login.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/login.spec.ts) |
| **Precondiciones** | Sesión cerrada; página de login abierta en `https://www.saucedemo.com` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Ingresar el usuario: `standard_user`.
2. Ingresar la contraseña: `secret_sauce`.
3. Hacer clic en el botón **Login**.

**Resultado Esperado:**

- El inicio de sesión es exitoso.
- La URL cambia a la página de inventario (`/inventory.html`).
- Se muestra el título "Products" y la lista de productos disponibles (6 productos). 

**Postcondiciones:** El usuario queda con la sesión iniciada. Cerrar sesión desde el menú (**Logout**) 
antes del siguiente caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| Inicio de sesión exitoso, la URL cambia a: `/inventory.html` y se muestran los productos | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-LGN-002 — Login con usuario bloqueado

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Login |
| **Requisito asociado** | REQ-001 |
| **Prioridad** | Alta |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`login.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/login.spec.ts) |
| **Precondiciones** | Sesión cerrada; página de login abierta en `https://www.saucedemo.com` |
| **Datos de Prueba** | Usuario: `locked_out_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Ingresar el usuario `locked_out_user`.
2. Ingresar la contraseña `secret_sauce`.
3. Hacer clic en el botón **Login**.

**Resultado Esperado:**

- No se inicia sesión.
- Se muestra un mensaje de error indicando que el usuario está bloqueado.
- El usuario permanece en la página de login y no se redirige a `/inventory.html`.

**Postcondiciones:** Ninguna, el sistema permanece sin sesión iniciada y no requiere limpieza.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| No inicia sesión, se muestra el mensaje "Sorry, this user has been locked out.", el usuario permanece en el login. | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-LGN-003 — Login con contraseña incorrecta

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Login |
| **Requisito asociado** | REQ-001 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`login.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/login.spec.ts) |
| **Precondiciones** | Sesión cerrada; página de login abierta en `https://www.saucedemo.com` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `incorrecta` |

**Pasos:**

1. Ingresar el usuario `standard_user`.
2. Ingresar la contraseña `incorrecta`.
3. Hacer clic en el botón **Login**.

**Resultado Esperado:**

- No se inicia sesión.
- Se muestra un mensaje de error indicando que el usuario y la contraseña no coinciden con ningún usuario registrado.
- El usuario permanece en la página de login y no se redirige a `/inventory.html`.

**Postcondiciones:** Ninguna, el sistema permanece sin sesión iniciada y no requiere limpieza.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| No se inicia sesión, se muestra el mensaje 'Username and password do not match any user in this service', 
el usuario permanece en el login | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-LGN-004 — Login con usuario vacío

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Login |
| **Requisito asociado** | REQ-001 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`login.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/login.spec.ts) |
| **Precondiciones** | Sesión cerrada; página de login abierta en `https://www.saucedemo.com` |
| **Datos de Prueba** | Usuario: vacío / Contraseña: `secret_sauce` |

**Pasos:**

1. Dejar el campo de usuario vacío.
2. Ingresar la contraseña `secret_sauce`.
3. Hacer clic en el botón **Login**.

**Resultado Esperado:**

- No se inicia sesión.
- Se muestra un mensaje de error indicando que el usuario es obligatorio.
- El usuario permanece en la página de login y no se redirige a `/inventory.html`.

**Postcondiciones:** Ninguna, el sistema permanece sin sesión iniciada y no requiere limpieza.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| No se inicia sesión, se muestra el mensaje: 'Username is required', el usuario permanece en el login | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-LGN-005 — Login con contraseña vacía

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Login |
| **Requisito asociado** | REQ-001 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`login.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/login.spec.ts) |
| **Precondiciones** | Sesión cerrada; página de login abierta en `https://www.saucedemo.com` |
| **Datos de Prueba** | Usuario: `standard_user`/ Contraseña: vacía |

**Pasos:**

1. Ingresar el usuario `standard_user`.
2. Dejar el campo de contraseña vacía.
3. Hacer clic en el botón **Login**.

**Resultado Esperado:**

- No se inicia sesión.
- Se muestra un mensaje de error indicando que la contraseña es obligatoria.
- El usuario permanece en la página de login y no se redirige a `/inventory.html`.

**Postcondiciones:** Ninguna, el sistema permanece sin sesión iniciada y no requiere limpieza.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| No se inicia sesión, se muestra el mensaje: 'Password is required', el usuario permanece en el login | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-LGN-006 — Login con usuario inexistente

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Login |
| **Requisito asociado** | REQ-001 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`login.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/login.spec.ts) |
| **Precondiciones** | Sesión cerrada; página de login abierta en `https://www.saucedemo.com` |
| **Datos de Prueba** | Usuario: `usuario_inexistente` / Contraseña: `secret_sauce` |

**Pasos:**

1. Ingresar el usuario `usuario_inexistente`.
2. Ingresar la contraseña `secret_sauce`.
3. Hacer clic en el botón **Login**.

**Resultado Esperado:**

- No se inicia sesión.
- Se muestra un mensaje de error indicando que el usuario y la contraseña no coinciden con ningún usuario registrado.
- El usuario permanece en la página de login y no se redirige a `/inventory.html`.

**Postcondiciones:** Ninguna, el sistema permanece sin sesión iniciada y no requiere limpieza.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| No se inicia sesión, se muestra el mensaje: 'Username and password do not match any user in this service', 
el usuario permanece en el login | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-INV-001 — Productos con imagen, nombre y precio visibles

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Inventario |
| **Requisito asociado** | REQ-002 |
| **Prioridad** | Alta |
| **Nivel** | E2E-UI |
| **Tipo** | Functional / Smoke |
| **¿Automatizable?** | Sí |
| **Automatización** | [`inventory.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/inventory.spec.ts) |
| **Precondiciones** | Sesión iniciada; página abierta en `https://www.saucedemo.com/inventory.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Observar la lista de productos en `/inventory.html`.
2. Verificar que cada producto muestre imagen, nombre, descripción y precio.
3. Verificar que la imagen corresponda al producto (no se repite la misma imagen en productos distintos).
4. Hacer clic en el nombre de un producto.
5. Verificar que el detalle muestre la imagen, el nombre, el precio y la descripción del mismo producto, y que la URL tenga el formato `/inventory-item.html?id=X`
(donde *X* es el *ID* numérico dinámico que corresponde al producto seleccionado).
6. Hacer clic en el botón **Back to products**.
7. Repetir los pasos 4 a 6 con al menos 2 productos más.

**Resultado Esperado:**

- Se muestran 6 productos, cada uno con imagen, nombre, descripción y precio.
- La imagen de cada producto corresponde a su nombre.
- El detalle coincide con la lista (mismo nombre y precio).
- La URL se actualiza al formato `/inventory-item.html?id=X`.
- Al regresar, el usuario vuelve a `/inventory.html`.

**Postcondiciones:** El usuario permanece en `/inventory.html` para el siguiente caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| Cada producto cuenta con imagen, nombre, descripción y precio diferente, se puede consultar el detalle y el detalle coincide con la lista, la URL se actualiza
dependiendo del producto y al regresar vuelve a `/inventory.html` | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-INV-002 — Ordenar por precio de menor a mayor

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Inventario |
| **Requisito asociado** | REQ-003 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`inventory.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/inventory.spec.ts) |
| **Precondiciones** | Sesión iniciada; página abierta en `https://www.saucedemo.com/inventory.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el menú desplegable de ordenamiento (que por defecto está en "Name (A to Z)").
2. Seleccionar la opción **Price (low to high)**.

**Resultado Esperado:**

- Los precios de los productos se muestran en orden ascendente (de menor a mayor). *(Ejemplo del estado actual (19/11/2026): empieza por la prenda infantil "Onesie" y termina en la "Fleece Jacket").
- El menú de ordenamiento se actualiza y muestra la opción **Price (low to high)** seleccionada.

**Postcondiciones:** El usuario permanece en la página de `/inventory.html` y debe seleccionar el ordenamiento nuevamente a **Name (A to Z)** para el próximo caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| "El menú desplegable de ordenamiento abre correctamente, al seleccionar el ordenamiento se muestran los productos con menor precio empezando por 
"Sauce Labs Onesie" y termina con el "Sauce Labs Fleece Jacket" | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-INV-003 — Ordenar por nombre de Z a A

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Inventario |
| **Requisito asociado** | REQ-003 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`inventory.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/inventory.spec.ts) |
| **Precondiciones** | Sesión iniciada; página abierta en `https://www.saucedemo.com/inventory.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el menú desplegable de ordenamiento (que por defecto está en **"Name (A to Z)"**).
2. Seleccionar la opción **Name (Z to A)**.

**Resultado Esperado:**

- Los productos se muestran en orden descendente (del que empieza con Z al que empieza con A). 
  *(Ejemplo del estado actual: empieza por la prenda "Test.allTheThings" y termina en la "Sauce Labs Backpack").*
- El menú de ordenamiento se actualiza y muestra la opción **Name (Z to A)** seleccionada.

**Postcondiciones:** El usuario permanece en la página de `/inventory.html` y debe seleccionar el ordenamiento nuevamente a **Name (A to Z)** para continuar con el próximo caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| El menú desplegable de ordenamiento abre correctamente, al seleccionar el ordenamiento se muestran los productos por
orden alfabetico empezando por 'Test.allTheThings() T-Shirt (Red) y termina en la "Sauce Labs Backpack' | Pass | N/A | 20/11/2026 | Yair Uriel García González |

---

### TC-CAR-001 — Agregar un producto al carrito

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Carrito |
| **Requisito asociado** | REQ-004 |
| **Prioridad** | Alta |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`inventory.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/inventory.spec.ts) |
| **Precondiciones** | Sesión iniciada; página abierta en `https://www.saucedemo.com/inventory.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el botón **Add to cart** de cualquier producto.
2. Verificar que el ícono del carrito muestre un contador en `1`.
3. Abrir el carrito (haciendo clic en el ícono).
4. Validar que el producto seleccionado es el que se muestra en la lista.
5. Hacer clic en el botón **Continue Shopping** para regresar al inventario.
6. Opcional, agregar un segundo producto y verificar que el contador pase a 2.

**Resultado Esperado:**

- El producto se agrega al carrito correctamente y el contador visual (badge) se actualiza a `1`.
- Al abrir el carrito, la URL cambia a `/cart.html` y se visualiza el producto agregado.
- Al hacer clic en el botón **Continue Shopping**, el usuario regresa a la página de inventario.

**Postcondiciones:** El usuario permanece en la página de `/inventory.html` para continuar con el próximo caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| | Draft | N/A | | |

---

### TC-CAR-002 — Quitar un producto del carrito

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Carrito |
| **Requisito asociado** | REQ-004 |
| **Prioridad** | Alta |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`inventory.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/inventory.spec.ts) |
| **Precondiciones** | Usuario con sesión iniciada y un producto en el carrito. |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Abrir el carrito.
2. Hacer clic en el botón **Remove** junto al producto.

**Resultado Esperado:**

- El producto desaparece del carrito.
- El contador del carrito vuelve a 0.

**Postcondiciones:** El carrito queda vacío.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| | Draft | N/A | | |

---

### TC-CHK-001 — Compra completa con datos válidos

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Checkout |
| **Requisito asociado** | REQ-005 |
| **Prioridad** | Alta |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`checkout.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/checkout.spec.ts) |
| **Precondiciones** | Sesión iniciada con standard_user, un producto agregado y la página en `/cart.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el botón **Checkout**.
2. Ingresar en **First Name:** `Ana`.
3. Ingresar en **Last Name:** `Pérez`. 
4. Ingresar en **Zip / Postal Code:** `55000`.
5. Hacer clic en el botón **Continue**.
6. Hacer clic en el botón **Finish**.

**Resultado Esperado:**

- Al hacer clic en **Checkout**, la URL cambia a `/checkout-step-one.html` y se muestra el formulario con **First Name**, **Last Name** y **Zip / Postal Code**.
- Al hacer clic en **Continue**, la URL cambia a `/checkout-step-two.html` y se muestran los productos agregados con su precio, el subtotal, los impuestos y el total de la compra.
- Al hacer clic en **Finish**, la URL cambia a `/checkout-complete.html`.
- Se muestra un mensaje de agradecimiento por el pedido.
- Se muestra un botón para regresar al inicio.

**Postcondiciones:**  El usuario tiene que iniciar sesión y volver a agregar artículos al carrito para el próximo caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| | Draft | N/A | | |

---

### TC-CHK-002 — Checkout con apellido vacío

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Checkout |
| **Requisito asociado** | REQ-006 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`checkout.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/checkout.spec.ts) |
| **Precondiciones** | Sesión iniciada con standard_user, un producto agregado y la página en `/cart.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el botón **Checkout**.
2. Ingresar en **First Name:** `Ana`.
3. Dejar el campo de **Last Name** vacío. 
4. Ingresar en **Zip / Postal Code:** `55000`.
5. Hacer clic en el botón **Continue**.


**Resultado Esperado:**

- No se finaliza el pedido.
- Se muestra un mensaje de error indicando que el **apellido** es obligatorio.
- El usuario permanece en la página de `/checkout-step-one.html`.


**Postcondiciones:** El usuario permanece en la página de `/checkout-step-one.html` para el siguiente caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| | Draft | N/A | | |

---

### TC-CHK-003 — Checkout con nombre vacío

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Checkout |
| **Requisito asociado** | REQ-006 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`checkout.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/checkout.spec.ts) |
| **Precondiciones** | Sesión iniciada con standard_user, un producto agregado y la página en `/cart.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el botón **Checkout**.
2. Dejar el campo de **First Name** vacío.
3. Ingresar en **Last Name:** `Pérez` . 
4. Ingresar en **Zip / Postal Code:** `55000`.
5. Hacer clic en el botón **Continue**.


**Resultado Esperado:**

- No se finaliza el pedido.
- Se muestra un mensaje de error indicando que el **nombre** es obligatorio.
- El usuario permanece en la página de `/checkout-step-one.html`.


**Postcondiciones:** El usuario permanece en la página de `/checkout-step-one.html` para el siguiente caso.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| | Draft | N/A | | |

---

### TC-CHK-004 — Checkout con código postal vacío

| Campo | Valor |
| :--- | :--- |
| **Módulo/Feature** | Checkout |
| **Requisito asociado** | REQ-006 |
| **Prioridad** | Media |
| **Nivel** | E2E-UI |
| **Tipo** | Functional |
| **¿Automatizable?** | Sí |
| **Automatización** | [`checkout.spec.ts`](https://github.com/YaUriGarcia/playwright-e2e-saucedemo/blob/main/tests/checkout.spec.ts) |
| **Precondiciones** | Sesión iniciada con standard_user, un producto agregado y la página en `/cart.html` |
| **Datos de Prueba** | Usuario: `standard_user` / Contraseña: `secret_sauce` |

**Pasos:**

1. Hacer clic en el botón **Checkout**.
2. Ingresar en **First Name:** `Ana`.
3. Ingresar en **Last Name:** `Pérez` . 
4. Dejar el campo de **Zip / Postal Code:** vacío.
5. Hacer clic en el botón **Continue**.


**Resultado Esperado:**

- No se finaliza el pedido.
- Se muestra un mensaje de error indicando que el **código postal** es obligatorio.
- El usuario permanece en la página de `/checkout-step-one.html`.


**Postcondiciones:** El usuario permanece en la página de `/checkout-step-one.html`.

**Ejecución:**

| Resultado Real | Estado | Defecto ID | Fecha | Ejecutado por |
| :--- | :--- | :--- | :--- | :--- |
| | Draft | N/A | | |

---

## Ejecuciones adicionales con otros usuarios

| Caso base | Usuario | Resultado Real | Estado | Defecto ID |
| :--- | :--- | :--- | :--- | :--- |
| TC-INV-001 | `problem_user` | | Draft | N/A |
| TC-INV-002 | `problem_user` | | Draft | N/A |
| TC-CAR-001 | `problem_user` | | Draft | N/A |
| TC-CAR-002 | `problem_user` | | Draft | N/A |
| TC-CHK-001 | `problem_user` | | Draft | N/A |
| TC-CHK-002 | `problem_user` | | Draft | N/A |

