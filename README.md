# **ms-eureka-server**

## **Descripción General**
El microservicio **ms-eureka-server** es el componente central encargado del descubrimiento dinámico de servicios en la arquitectura de **Relatos de Papel**. Su función principal es permitir que los microservicios se registren automáticamente y que otros componentes puedan descubrirlos fácilmente sin necesidad de configuraciones estáticas. Esto facilita la escalabilidad, resiliencia y flexibilidad del sistema.

## **Características Principales**
- **Registro dinámico de servicios:** Los microservicios pueden registrarse y actualizar su estado de manera automática.
- **Descubrimiento de servicios:** Otros microservicios pueden buscar y conectarse dinámicamente con los servicios registrados.
- **Alta disponibilidad (opcional):** En entornos de producción, puede configurarse para operar en modo de replicación.
- **Interfaz web de monitoreo:** Permite ver el estado de los servicios registrados y monitorear la salud de los mismos.

---

## **Configuración Importante**
- **Nombre de la aplicación:** Se identifica como **ms-eureka-server** dentro del ecosistema de servicios.
- **Puerto predeterminado:** El servidor escucha en el puerto **8761**.
- **No se registra consigo mismo:** Este servidor actúa únicamente como punto central y no participa como cliente.

## **Comportamiento de Registro y Descubrimiento**
- Los microservicios como **ms-books-catalogue** y **ms-books-payments** se registran automáticamente en **Eureka Server** al iniciar, indicando su estado y ubicación.
- Cuando un microservicio necesita consumir otro, consulta la información del registro dinámico en **Eureka** para obtener la dirección más reciente de la instancia deseada.
- Si una instancia deja de estar disponible, **Eureka** la elimina del registro después de un período de inactividad (configurable).

---

## **Pasos para Desplegar el Proyecto**
1. **Clonar el repositorio:** https://github.com/Angelica-Quevedo-unir/ms-eureka-server.
2. **Configurar las propiedades:** Verifica que las propiedades del servidor estén adecuadas para tu entorno.
3. **Construir el proyecto:** Usa Maven para empaquetar la aplicación.


4. **Ejecutar el servidor:** Inicia el servidor y verifica su disponibilidad accediendo a su interfaz web.

```
mvn clean package
mvn spring-boot:run 
```

## **Acceso a la Interfaz Web**
Una vez iniciado, puedes acceder a la interfaz de **Eureka Server** en la siguiente dirección:

```
http://localhost:8761
```

Desde esta interfaz, puedes:
- Monitorear los servicios registrados.
- Ver el estado de las instancias.
- Comprobar la disponibilidad de los microservicios.

---

## **Despliegue en Producción**
Para entornos de producción, se recomienda:
- Ejecutar múltiples instancias de **Eureka Server** en modo de replicación.
- Configurar tiempos de heartbeat y latencia para tolerar fallas.
- Asegurarse de que los microservicios se conecten a múltiples servidores de Eureka para mayor disponibilidad.

