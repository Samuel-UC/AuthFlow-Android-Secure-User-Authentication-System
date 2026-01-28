# 📱 AuthFlow-Android: Sistema de Autenticación de Usuarios Seguro

[![Plataforma: Android](https://img.shields.io/badge/Plataforma-Android-green.svg)](https://developer.android.com/)
[![Lenguaje: Kotlin](https://img.shields.io/badge/Lenguaje-Kotlin-purple.svg)](https://kotlinlang.org/)
[![UI: Material Design 3](https://img.shields.io/badge/UI-Material_3-blue.svg)](https://m3.material.io/)
[![Arquitectura: MVVM](https://img.shields.io/badge/Arquitectura-MVVM-red.svg)](https://developer.android.com/topic/libraries/architecture/viewmodel)
[![Licencia: MIT](https://img.shields.io/badge/Licencia-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Descripción General
**AuthFlow-Android** es una aplicación móvil de alto rendimiento diseñada para gestionar el acceso e identidad de los usuarios. Desarrollada de forma nativa para Android, este proyecto presenta una implementación profesional de los flujos de trabajo de **Registro de Usuarios** e **Inicio de Sesión**.

La aplicación se centra en la seguridad y la capacidad de respuesta, utilizando una arquitectura **MVVM (Model-View-ViewModel)** para desacoplar la lógica de negocio de la interfaz de usuario. Proporciona una transición fluida entre los estados de autenticación y garantiza que los datos del usuario se validen mediante un riguroso filtro de front-end antes de ser procesados.

---

## 🚀 Características Clave
* **UI/UX Moderna:** Construida con componentes de Material Design 3 para una sensación elegante, responsiva y nativa.
* **Validación en Tiempo Real:** Retroalimentación instantánea sobre la entrada del usuario (formato de correo, fuerza de la contraseña y campos obligatorios).
* **Gestión de Estado Segura:** Utiliza ViewModels y LiveData/Flow para mantener el estado de la interfaz durante cambios de configuración (como la rotación de pantalla).
* **Manejo de Errores:** Notificaciones integradas mediante Toast y Snackbar para una retroalimentación intuitiva sobre fallos de autenticación.
* **Arquitectura de Navegación:** Transiciones optimizadas entre Activity/Fragment para un recorrido fluido desde el registro hasta el inicio de sesión.

---

## 🛠️ Aspectos Técnicos Destacados

### 1. Validación Robusta de Entradas
El sistema emplea una lógica de validación centralizada para garantizar la integridad de los datos antes de cualquier interacción con la red o la base de datos.

```kotlin
// Ejemplo de lógica de validación reactiva
fun isEmailValid(email: String): Boolean {
    return android.util.Patterns.EMAIL_ADDRESS.matcher(email).matches()
}

fun validateCredentials(pass: String): Boolean {
    // Requiere al menos 8 caracteres y complejidad alfanumérica
    val passwordPattern = "^(?=.*[0-9])(?=.*[a-z]).{8,}$".toRegex()
    return passwordPattern.containsMatchIn(pass)
}

```

### 2. Arquitectura View-Model

Para evitar la pérdida de datos y garantizar un ciclo de vida limpio, el proyecto se adhiere al patrón MVVM.

```kotlin
class AuthViewModel : ViewModel() {
    private val _authState = MutableLiveData<AuthState>()
    val authState: LiveData<AuthState> = _authState

    fun loginUser(credentials: UserCredentials) {
        // Lógica de autenticación asíncrona
        _authState.value = AuthState.Loading
        // Proceder con la verificación segura...
    }
}

```

### 3. Composición de la Interfaz (UI)

Los diseños están optimizados utilizando `ConstraintLayout` para reducir la profundidad de la jerarquía de vistas, mejorando significativamente el rendimiento de renderizado en dispositivos de gama media y baja.

---

## 📂 Estructura del Proyecto

```text
AuthFlow-Android/
├── app/
│   ├── src/main/
│   │   ├── java/com/authflow/
│   │   │   ├── ui/             # Activities, Fragments y Adapters
│   │   │   ├── viewmodel/      # Gestión de Estado de la UI
│   │   │   └── data/           # Modelos y Repositorios
│   │   └── res/layout/         # Definiciones de Layout en XML
├── build.gradle                # Dependencias a nivel de proyecto
└── README.md                   # Documentación

```

---

## 🔧 Instalación y Configuración

1. **Clonar el repositorio:**
```bash
git clone [https://github.com/tu-usuario/AuthFlow-Android.git](https://github.com/tu-usuario/AuthFlow-Android.git)

```


2. **Abrir en Android Studio:**
Selecciona "Open an Existing Project" y apunta al directorio clonado.
3. **Sincronizar Gradle:**
Espera a que el IDE descargue las dependencias (Material, Lifecycle, etc.).
4. **Ejecutar:**
Selecciona un emulador (API 24+) o un dispositivo físico y haz clic en **Run 'app'**.

---

## 🎮 Flujo de Navegación

| Pantalla | Responsabilidad |
| --- | --- |
| **Inicio de Sesión** | Verificación de credenciales y punto de entrada de sesión. |
| **Registro** | Creación de cuenta nueva con validación campo por campo. |
| **Dashboard** | Zona de aterrizaje segura tras una autenticación exitosa. |
| **Recuperación** | (Opcional) Flujo de trabajo para restauración de cuenta. |

---

## 📈 Objetivos de Aprendizaje

Este proyecto demuestra competencia en:

* **Framework de Android:** Uso experto de Activities, Intents y componentes del ciclo de vida.
* **Programación Reactiva:** Implementación de observadores para manejar actualizaciones de UI asíncronas.
* **Diseño de UI Seguro:** Enmascaramiento de entradas sensibles y gestión de interacciones con el teclado virtual.
* **Arquitectura Limpia (Clean Architecture):** Organización de código para mantenibilidad y escalabilidad.

---

## 📄 Licencia

Este proyecto está bajo la **Licencia MIT**.

**Desarrollado por Samuel Upegui Cardona.**
*"Diseñando accesos seguros para la era móvil."*

```

```