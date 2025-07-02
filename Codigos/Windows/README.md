# Documentación Técnica: Driver de Monitoreo de DLLs/EXEs

## 📌 Descripción General
Driver de kernel para Windows que monitorea la carga de imágenes (DLLs/EXEs) mediante callbacks y envía datos a un servidor remoto (fines educativos).

---

## 🏗️ Estructura del Código

### 1. **DriverEntry (Punto de Entrada)**
```c
NTSTATUS DriverEntry(PDRIVER_OBJECT DriverObject, PUNICODE_STRING RegistryPath) {
    PsSetLoadImageNotifyRoutine(ImageLoadCallback);
    DriverObject->DriverUnload = UnloadDriver;
    return STATUS_SUCCESS;
}
