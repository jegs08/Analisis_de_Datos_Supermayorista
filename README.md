<div align="center">
  <h1>Análisis de datos con Power BI</h1>
</div>

<div align="center"> 
  <img src="readme_img/Microsoft-Power-BI-analisis.png" width="">
</div>

## Introducción al documento

El contenido de este documento son **apuntes teoricos y prácticos** y un proyecto de **Análisis de datos** de una tienda llamada **"SUPERMAYORISTA"** y busca ser una guía para futuros trabajos personales. El mismo está hecho por mi persona [José Eduardo Galván Salvador](https://www.linkedin.com/in/eduardo-galvan1208/) para el grupo de estudio [Data Growth Community](https://www.linkedin.com/company/datagrowthcommunity/).

## Objetivos del documento

- Ejecutar operaciones básicas de Pandas.
- Comprender el significado y uso de los DataFrames en Ciencia de Datos.
- Usar Computational Tools de Pandas para realizar cálculos básicos.
- Trabajar con Statisticals tools.
- Hacer preprocesamiento de datos para crear modelos. 
- Extraer información de Data Sets usando Time Series y Date Functionality.

## Tabla de contenido
- [Planificación del proyecto](#Planificación-del-proyecto)
  - [Alcance del negocio](#Alcance-del-negocio)
- [Definición de requerimientos para la empresa SUPERMAYORISTA](#Definición-de-requerimientos-para-la-empresa-SUPERMAYORISTA)
  - [Requisitos del negocio](#Requisitos-del-negocio)
  - [Base de Datos transaccional en SQL Server](#Base-de-Datos-transaccional-en-SQL-Server)
  - [Diccionario de datos del origen a nivel general de la base de datos transaccional en SQL Server 2017](#Diccionario-de-datos-del-origen-a-nivel-general-de-la-base-de-datos-transaccional-en-SQL-Server-2017)
    - [Tablas](#Tablas)
    - [Diccionario de datos de la base de datos transaccional en SQL Server 2017](#Diccionario-de-datos-de-la-base-de-datos-transaccional-en-SQL-Server-2017)
- [Modelo Dimensional](#Modelo-Dimensional)
  - [Elección de dimensiones](#Elección-de-dimensiones)
- [Dimensiones encontradas](#Dimensiones-encontradas)
- [Diseño lógico](#Diseño-lógico)
- [Diseño físico](#Diseño-físico)
  - [Tablas del modelo dimensional](#Tablas-del-modelo-dimensional)


## Planificación del proyecto

### Alcance del negocio

El presente proyecto busca ayudar con la gestión del área de ventas de la empresa SuperMayorista mediante informes de análisis de la información completos, veraces y en tiempo real que permita apoyar en la toma de decisiones.

## Definición de requerimientos para la empresa SUPERMAYORISTA

### Requisitos del negocio

<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-01</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N V VS T</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"El total de ventas por periodo"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Producto</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Más vendidos</i></td>
        </tr>
    </tbody>
</table>


<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-02</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N PROD</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"Cuáles fueron los productos más vendidos"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Periodo</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Cantidad de ventas</i></td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-03</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N VE</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"Quiénes fueron los vendedores con las mayores ventas realizadas"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Vendedor</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Mayor cantidad de ventas</i></td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-04</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N S VS F</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"Quiénes fueron los supervisores que tuvieron baja efectividad (cantidad de ventas en cuerto periodo)"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Vendedor</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Cantidad de ventas</i></td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-05</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N V AND C</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"Cuál es la zona con maores ventas y mayores cantidades de productos vendidos"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Zona</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Mayor cantidad de ventas, mayor cantidad de productos vendidos</i></td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-06</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N B VS AC</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"Cuál es el banco más factible para solicitar un ajuste de comisión"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Banco</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Mayor comisión obtenida por las ventas</i></td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <th><strong>Identificador</strong></th>
            <th><i>R-07</i></th>
            <th><strong>Nombre</strong></th>
            <th><i>TOP N VE VS V AND C AND M</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>Tipo</strong></td>
            <td align="center"><i>Funcional</i></td>
            <td align="center"><strong>Fecha</strong></td>
            <td align="center"><i>08/12/2022</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Prioridad</strong></td>
            <td align="center"><i>Alta</i></td>
            <td align="center"><strong>Necesidad</strong></td>
            <td align="center"><i>Si</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Descripción</strong></td>
            <td colspan=3 align="center"><i>"El top de los vendedores que más comisionan por ventas"</i></td>
        </tr>
        <tr>
            <td align="center"><strong>Datos dimensionales</strong></td>
            <td align="center"><i>Vendedor</i></td>
            <td align="center"><strong>Datos Hechos</strong></td>
            <td align="center"><i>Mayor comisión obtenida en base a la venta</i></td>
        </tr>
    </tbody>
</table>

### Base de Datos transaccional en SQL Server

<div align="center"> 
  <img src="readme_img/fig_1.png" width="">
</div>

### Diccionario de datos del origen a nivel general de la base de datos transaccional en SQL Server 2017

<table>
    <thead>
        <tr>
            <th>Tabla</th>
            <th>Descripción</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td align="center"><strong>VENTA</strong></td>
            <td align="center"><i>Se registran los movimiento de las ventas realizadas.</i></td>
        </tr>
        <tr>
            <td align="center"><strong>DETALLE_VENTA</strong></td>
            <td align="center"><i>Se registran los detalle de las ventas realizadas.</i></td>
        </tr>
        <tr>
            <td align="center"><strong>PRODUCTO</strong></td>
            <td align="center"><i>Se registran los productos de la empresa.</i></td>
        </tr>
        <tr>
            <td align="center"><strong>CLIENTE</strong></td>
            <td align="center"><i>Se registran los clientes de la empresa.</i></td>
        </tr>
        <tr>
            <td align="center"><strong>VENDEDOR</strong></td>
            <td align="center"><i>Se registran los vendedores de la empresa.</i></td>
        </tr>
        <tr>
            <td align="center"><strong>TIPO_DOCUMENTO</strong></td>
            <td align="center"><i>Se registran los tipos de documentos que maneja la empresa.</i></td>
      </tr>
    </tbody>
</table>

#### Tablas

#### Diccionario de datos de la base de datos transaccional en SQL Server 2017

### Modelo Dimensional

#### Elección de dimensiones

### Dimensiones encontradas

### Diseño lógico

### Diseño físico

#### Tablas del modelo dimensional

