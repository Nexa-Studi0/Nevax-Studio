# Nexa Studio

Estudio web local para prototipar videojuegos 2D y 3D desde el navegador.

## Iniciar

```bash
npm install
npm run dev
```

Vite muestra la URL local al iniciar. Para crear una compilación de producción, usa `npm run build`.

## Funciones

- Proyectos desde plantillas 2D/3D, con apertura, duplicación, renombrado, eliminación, importación y exportación JSON.
- Escena Three.js con jerarquía, cuadrícula, cámara orbital, selección, transformaciones e inspector.
- Interfaz adaptable a escritorio, tablet y móvil; los paneles laterales se abren por separado en pantallas pequeñas.
- Vista de juego con WASD, carrera, salto y cámara con ratón en escritorio; controles táctiles y cámara por arrastre en móvil. También incluye pausa, reinicio y atajos configurables.
- Editor Monaco para HTML, CSS y JavaScript, con vista previa en sandbox y salida de consola.
- Biblioteca local de recursos y control de versiones básico con commits y ramas locales.

## Almacenamiento y servicios

Los datos se guardan en `localStorage` del navegador y no salen de este dispositivo. Exporta una copia JSON para mover o respaldar un proyecto. La capacidad del almacenamiento del navegador limita el tamaño de los proyectos y recursos.

El historial no se sincroniza con GitHub u otro remoto. Publicar, compartir enlaces, sincronizar ramas o conectar repositorios requiere un servicio y credenciales que esta versión no configura. No se afirma que haya cambios subidos.

La previsualización de código se ejecuta en un `iframe` con sandbox y no comparte el almacenamiento del estudio.

La vista 3D necesita un navegador moderno con WebGL habilitado. Si el dispositivo no puede inicializar WebGL, el estudio muestra un aviso y mantiene accesibles el código y los archivos.

## Inicio de sesión Google/GitHub

La autenticación usa Supabase Auth OAuth. Para activarla:

1. Crea un proyecto Supabase y habilita Google y GitHub en **Authentication → Providers** con las credenciales OAuth de cada proveedor.
2. En la configuración de autenticación de Supabase, añade el callback `https://<project-ref>.supabase.co/auth/v1/callback` en cada proveedor y permite la URL del estudio en **URL Configuration → Redirect URLs** (por ejemplo, `http://localhost:4173/**` y el origen de producción).
3. Copia `.env.example` como `.env.local` y define `VITE_SUPABASE_URL` y `VITE_SUPABASE_ANON_KEY` con los valores del proyecto. Reinicia Vite.

El SDK conserva la sesión OAuth en el navegador y permite cerrar sesión. No uses una clave `service_role` en el cliente. Sin esas variables, o si los proveedores no están habilitados, los botones se muestran desactivados y el diálogo explica lo que falta. La cuenta autenticada no sincroniza ni publica los proyectos locales.
