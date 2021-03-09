# Análisis_SSM
Se muestra la forma de analizar, visualizar y conocer los detalles de los productos de humedad del suelo a través de Rstudio


# Código en Rstudio 

Se guarda la información

> setwd("~/Análisis de Tesis en Rstudio y SAGA GIS/Variables/Humedad/SSM_Bir/1_Enero")

*carga libreria*
Se necesito cargar una librería raster

##### Raster 

```library(raster)```

Se instala el paquete "ncdf4"

> install.packages("ncdf4")

*#Datos de Humedad*

Luego se cargan las imagenes raster humedad de suelo y el ruido de humedad de suelo que genera.

##### Humedad de suelo

```ssm<- raster('c_gls_SSM1km_201901010000_CEURO_S1CSAR_V1.1.1.nc', varname="ssm")```

```plot(ssm)```

Luego se consulto las proyecciones del producto

```[1] "+proj=longlat +ellps=WGS84 +no_defs"```
```> ssm```
```class      : RasterLayer```
```dimensions : 4144, 6832, 28311808  (nrow, ncol, ncell)```
```resolution : 0.008928571, 0.008928571  (x, y)```
```extent     : -11, 50, 35, 72  (xmin, xmax, ymin, ymax)```
```crs        : +proj=longlat +ellps=WGS84 +no_defs``` 
```source     :``` ```C:/Users/Usuario/Documents/R/Pruebas/Humedad/c_gls_SSM1km_201901010000_CEURO_S1CSAR_V1.1.1.nc ```
```names      : Surface.Soil.Moisture ```
```z-value    : 2018-12-31``` 
```zvar       : ssm```

###### Ruido de la Humedad de suelo

 >ssm_noise <- raster('c_gls_SSM1km_201901010000_CEURO_S1CSAR_V1.1.1.nc', varname="ssm_noise" )
 
>plot(ssm_noise)

>projection(ssm_noise)

De estos era necesario conocer las pendiente y la orientación.

```x <- terrain(DEM, opt=c('slope', 'aspect'), unit='degrees')```
```plot(x)```

Para visualizarlo, se cargo el mapa mundial, para conocer la zona donde se mostraba la humedad
>#Pac

>library(maps)

>map("world",add=T)


## Imagen 


