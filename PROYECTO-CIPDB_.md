<img src="Logo_UCO.png" style="width:1in" />
<img src="facultad%20ciencias.jpg" style="width:1in" />

Genómica de la sensibilidad a los fármacos en el cáncer

================
Ortiz G <b02orpeg@uco.es>Montes D <b92mobad@uco.es>Ferrer L
<b02feril@uco.es>
2024-12-05

- [1. Introducción](#1-introducción)
  - [1.1 Datos](#11-datos)
  - [1.2 Variables](#12-variables)
  - [1.3 Uso de Fármacos en el Cáncer](#13-uso-de-fármacos-en-el-cáncer)
- [2. Materiales y Métodos](#2-materiales-y-métodos)
- [3. Objetivos](#3-objetivos)
  - [3.1 Objetivo General](#31-objetivo-general)
  - [3.2 Objetivos Específicos](#32-objetivos-específicos)
- [4. Hipótesis](#4-hipótesis)
- [5. Resultados](#5-resultados)
  - [5.1 Relación entre las variables: ***Fármaco***, ***Línea
    Celular*** y
    ***AUC***](#51-relación-entre-las-variables-fármaco-línea-celular-y-auc)
  - [5.2. Relación entre las variables ***Fármaco***, ***Línea
    Celular*** y
    ***LN-IC50***](#52-relación-entre-las-variables-fármaco-línea-celular-y-ln-ic50)
  - [5.3 Relación entre las variables ***Fármaco***, ***Línea Celular***
    y
    ***Z-Score***](#53-relación-entre-las-variables-fármaco-línea-celular-y-z-score)
- [6. Conclusiones](#6-conclusiones)
- [7. Referencias y bibliografía](#7-referencias-y-bibliografía)

<!-- cargamos las librerias que vamos a utilizar, queremos que el código se ejecute, pero no que aparezca en en nuestro documento final, también excluímos los avisos y mensajes -->

## 1. Introducción

El conjunto de datos <span style="color: blue;">***Genómica de la
sensibilidad a los fármacos en el cáncer***</span> (GDSC) constituye una
herramienta clave para identificar **biomarcadores terapéuticos** en
estudios sobre el **cáncer**. Este recurso integra información sobre la
respuesta a medicamentos con perfiles genómicos de líneas celulares de
cáncer, facilitando el análisis de la relación entre las
**características genéticas** y la susceptibilidad a los **tratamientos
farmacológicos** ([Alipour 2024](#ref-gdsc_genomics_2024)).

### 1.1 Datos

A continuación, se muestra la **tabla de datos** analizada en este
proyecto.

|  DRUG_NAME   | CELL_LINE_NAME |  LN_IC50  |   AUC    |  Z_SCORE  |
|:------------:|:--------------:|:---------:|:--------:|:---------:|
| Camptothecin |     PFSK-1     | -1.463887 | 0.930220 | 0.433123  |
| Camptothecin |      ES5       | -3.360586 | 0.791072 | -0.599569 |
| Camptothecin |      ES7       | -5.044940 | 0.592660 | -1.516647 |
| Camptothecin |     EW-11      | -3.741991 | 0.734047 | -0.807232 |
| Camptothecin |    SK-ES-1     | -5.142961 | 0.582439 | -1.570016 |
| Camptothecin |    COLO-829    | -1.235034 | 0.867348 | 0.557727  |
| Camptothecin |      5637      | -2.632632 | 0.834067 | -0.203221 |
| Camptothecin |      RT4       | -2.963191 | 0.821438 | -0.383200 |
| Camptothecin |     SW780      | -1.449138 | 0.905050 | 0.441154  |
| Camptothecin |     TCCSUP     | -2.350633 | 0.843430 | -0.049682 |

Tabla 1: Diez primeras filas

### 1.2 Variables

- **DRUG_NAME**: esta variable te indica el nombre del medicamento que
  se está evaluando en las células malignas.

- **CELL_LINE_NAME**: La denominación de la línea de células tumorales
  empleada en nuestra investigación.

- **⁠LN_IC50**: Es el logaritmo natural de la concentración del
  medicamento necesaria para disminuir a la mitad la actividad biológica
  de las células. Un valor reducido de LN_IC50 indica que el medicamento
  es muy eficaz, ya que se requiere una pequeña dosis para generar un
  gran impacto. Un valor elevado sugiere que el medicamento es menos
  eficaz, puesto que se requiere mayor cantidad para lograr el mismo
  efecto.

- **⁠AUC**: El área bajo la curva (AUC) es un indicador que demuestra
  cuán eficaz es el medicamento para disminuir la actividad de las
  células tumorales. Cuanto más alto sea el AUC, más eficiente resulta
  el medicamento, puesto que señala que puede disminuir en mayor medida
  la actividad celular. Si el AUC es bajo, el medicamento no es tan
  eficaz.

- **⁠Z_SCORE**: Es una medida que indica cuán sensible es una línea
  celular a un medicamento en relación con otras líneas celulares. Un
  valor positivo de Z_SCORE sugiere que la línea celular responde al
  fármaco, mientras que un valor negativo sugiere resistencia. Cuanto
  mayor sea el Z_SCORE, más eficaz resultará el medicamento para esa
  línea celular.

### 1.3 Uso de Fármacos en el Cáncer

**Ulixertinib** (Uso_Total: 1698) es el fármaco más utilizado en el
estudio. Sin embargo, encontramos otros fármacos, como **Docetaxel**
(NUM_CELL_LINES: 968), que han sido utilizados en una mayor cantidad de
líneas celulares.

|  DRUG_NAME   | USO_TOTAL | NUM_CELL_LINES |
|:------------:|:---------:|:--------------:|
| Ulixertinib  |   1698    |      963       |
| Oxaliplatin  |   1684    |      967       |
| Fulvestrant  |   1680    |      965       |
| Selumetinib  |   1666    |      967       |
| Dactinomycin |   1659    |      960       |
|  Docetaxel   |   1637    |      968       |
|    GSK343    |   1634    |      965       |
|  Uprosertib  |   1634    |      966       |
|   Acetalax   |   1434    |      717       |
|    MG-132    |    969    |      969       |

Tabla 2: Diez primeras filas

## 2. Materiales y Métodos

Los datos de este proyectos fueron descargados desde
[kaggle](https://www.kaggle.com). Para llevar a cabo el análisis se hizo
uso del programa Rstudio ([R Core Team 2024](#ref-R-base)) con las
librerías dplyr ([**R-dplyr?**](#ref-R-dplyr)) y ggplot
([**R-ggplot2?**](#ref-R-ggplot2);
[**ggplot22016?**](#ref-ggplot22016)). Para la realización de este
informe se han utilizado los paquetes: knitr
([**R-knitr?**](#ref-R-knitr); [**knitr2015?**](#ref-knitr2015);
[**knitr2014?**](#ref-knitr2014)), ([Grolemund and Wickham
2011](#ref-lubridate)), ([**forecats?**](#ref-forecats)), ([Wickham
2023](#ref-stringr)), ([Wickham and Henry 2023](#ref-purrr)), ([Müller
and Wickham 2023](#ref-tibble)), ([Wickham, Vaughan, and Girlich
2024](#ref-tidyr)).

## 3. Objetivos

A continuación, se presentan el **objetivo general** y los **objetivos
específicos** de este estudio.

### 3.1 Objetivo General

- Investigar las relaciones entre los perfiles genómicos de líneas
  celulares cancerosas y su sensibilidad a diferentes fármacos,
  utilizando el conjunto de datos Genómica de la sensibilidad a los
  fármacos en el cáncer (GDSC), para identificar biomarcadores que
  puedan guiar el desarrollo de terapias personalizadas en el
  tratamiento del cáncer.

### 3.2 Objetivos Específicos

- Explorar diferencias en la sensibilidad a fármacos entre diversos
  tipos de cáncer y sus perfiles genómicos.
- Identificar potenciales biomarcadores terapéuticos que puedan ser
  validados en investigaciones posteriores.

## 4. Hipótesis

La hipótesis planteada es la siguiente: <span style="color: blue;">**A
mayor uso de un fármaco en las líneas celulares estudiadas, mayor será
su eficacia en la inhibición del crecimiento celular**</span>.

## 5. Resultados

Se ha realizado un estudio estadístico para verificar la hipótesis
planteada con anterioridad. Para ello, se han tenido en cuenta las
variables cualitativas ***Fármaco*** y ***Línea Celular***, junto a las
variables cuantitativas ***AUC***, ***LNIC50*** y ***Z_SCORE***.

### 5.1 Relación entre las variables: ***Fármaco***, ***Línea Celular*** y ***AUC***

1.  **AUC**: Muestra cuánto de efectivo es un fármaco al medir su
    concentración a lo largo del tiempo ([Alipour
    2024](#ref-gdsc_genomics_2024)).
    - **Valores altos de AUC**: Mayor efectividad del fármaco.
    - **Valores bajos de AUC**: Menor efectividad.
2.  **Ejes**:
    - **Eje X**: Fármacos.
    - **Eje Y**: Líneas celulares.
3.  **Puntos**:
    - **Tamaño**: Mayor tamaño = mayor efectividad.
    - **Color**: Colores claros = mayor AUC (más efectivo), colores
      oscuros = menor AUC (menos efectivo).

<div class="figure" style="text-align: center">

<img src="PROYECTO-CIPDB_files/figure-gfm/Gráfico Fármaco, Línea celular y AUC-1.png" alt="Fig 1. Relación entre Fármaco, Línea celular y AUC"  />
<p class="caption">
Fig 1. Relación entre Fármaco, Línea celular y AUC
</p>

</div>

4.  **Interpretación**:
    - Puntos grandes y claros indican fármacos efectivos.
    - Puntos pequeños y oscuros indican fármacos menos efectivos.

### 5.2. Relación entre las variables ***Fármaco***, ***Línea Celular*** y ***LN-IC50***

1.  **LN_IC50**: Mide la concentración de un fármaco que inhibe el 50%
    de la actividad celular ([Alipour 2024](#ref-gdsc_genomics_2024)).
    - **Valores bajos de LN_IC50**: Mayor sensibilidad del fármaco.
    - **Valores altos de LN_IC50**: Menor sensibilidad (resistencia).
2.  **Ejes**:
    - **Eje X**: Fármacos.
    - **Eje Y**: Líneas celulares ordenadas por sensibilidad al fármaco.
3.  **Puntos**:
    - **Tamaño**: Mayor tamaño = mayor resistencia.
    - **Color**: Colores claros = mayor resistencia, colores oscuros =
      mayor sensibilidad.

<div class="figure" style="text-align: center">

<img src="PROYECTO-CIPDB_files/figure-gfm/Gráfico Fármaco, Línea celular y LN_IC50-1.png" alt="Fig 2. Relación entre Fármaco, Línea celular y LN_IC50"  />
<p class="caption">
Fig 2. Relación entre Fármaco, Línea celular y LN_IC50
</p>

</div>

4.  **Interpretación**:
    - Puntos pequeños y oscuros indican que las líneas celulares son más
      sensibles al fármaco.
    - Puntos grandes y claros indican resistencia al fármaco.

### 5.3 Relación entre las variables ***Fármaco***, ***Línea Celular*** y ***Z-Score***

1.  **Z_SCORE**: Mide la actividad de un fármaco en una línea celular en
    comparación con otros valores ([Alipour
    2024](#ref-gdsc_genomics_2024)).
    - **Valores altos de Z_SCORE**: Mayor actividad del fármaco.
    - **Valores bajos de Z_SCORE**: Menor actividad o resistencia.
2.  **Ejes**:
    - **Eje X**: Fármacos.
    - **Eje Y**: Líneas celulares ordenadas por Z_SCORE.
3.  **Puntos**:
    - **Tamaño**: Mayor tamaño = mayor actividad del fármaco.
    - **Color**: Diferencia entre fármacos usando colores.

<div class="figure" style="text-align: center">

<img src="PROYECTO-CIPDB_files/figure-gfm/Gráfico Fármaco, Línea celular y Z_SCORE-1.png" alt="Fig 3. Relación entre Fármaco, Línea celular y Z_SCORE"  />
<p class="caption">
Fig 3. Relación entre Fármaco, Línea celular y Z_SCORE
</p>

</div>

4.  **Interpretación**:
    - Puntos grandes indican fármacos activos en esa línea celular.
    - Puedes ver rápidamente qué fármacos tienen más actividad en qué
      líneas celulares.

## 6. Conclusiones

<span style="color: red;">**La hipótesis propuesta inicialmente no se
acepta**</span>. “A mayor uso de un fármaco en las líneas celulares
estudiadas, mayor será su eficacia en la inhibición del crecimiento
celular” no se sostiene con los gráficos analizados.

- En el **Gráfico 1 (AUC)**, no todos los fármacos más usados tienen una
  alta eficacia (AUC). Algunos fármacos comunes muestran baja
  efectividad.
- En el **Gráfico 2 (LN_IC50)**, fármacos con mayor uso pueden requerir
  mayores concentraciones para ser efectivos, lo que indica menor
  eficacia.
- En el **Gráfico 3 (Z_SCORE)**, no siempre los fármacos con mayor uso
  tienen la mayor actividad en todas las líneas celulares.

**Un mayor uso de un fármaco no garantiza una mayor eficacia en la
inhibición del crecimiento celular**

## 7. Referencias y bibliografía

    ## R version 4.3.2 (2023-10-31 ucrt)
    ## Platform: x86_64-w64-mingw32/x64 (64-bit)
    ## Running under: Windows 11 x64 (build 26100)
    ## 
    ## Matrix products: default
    ## 
    ## 
    ## locale:
    ## [1] LC_COLLATE=Spanish_Spain.utf8  LC_CTYPE=Spanish_Spain.utf8   
    ## [3] LC_MONETARY=Spanish_Spain.utf8 LC_NUMERIC=C                  
    ## [5] LC_TIME=Spanish_Spain.utf8    
    ## 
    ## time zone: Europe/Madrid
    ## tzcode source: internal
    ## 
    ## attached base packages:
    ## [1] stats     graphics  grDevices utils     datasets  methods   base     
    ## 
    ## other attached packages:
    ##  [1] knitr_1.45      lubridate_1.9.3 forcats_1.0.0   stringr_1.5.0  
    ##  [5] dplyr_1.1.3     purrr_1.0.2     readr_2.1.4     tidyr_1.3.0    
    ##  [9] tibble_3.2.1    tidyverse_2.0.0 ggplot2_3.4.4  
    ## 
    ## loaded via a namespace (and not attached):
    ##  [1] gtable_0.3.4      highr_0.10        compiler_4.3.2    tidyselect_1.2.0 
    ##  [5] scales_1.2.1      yaml_2.3.7        fastmap_1.1.1     R6_2.5.1         
    ##  [9] labeling_0.4.3    generics_0.1.3    munsell_0.5.0     pillar_1.9.0     
    ## [13] tzdb_0.4.0        rlang_1.1.2       utf8_1.2.4        stringi_1.7.12   
    ## [17] xfun_0.41         viridisLite_0.4.2 timechange_0.2.0  cli_3.6.1        
    ## [21] withr_2.5.2       magrittr_2.0.3    digest_0.6.33     grid_4.3.2       
    ## [25] rstudioapi_0.15.0 hms_1.1.3         lifecycle_1.0.3   vctrs_0.6.4      
    ## [29] evaluate_0.23     glue_1.6.2        farver_2.1.1      fansi_1.0.5      
    ## [33] colorspace_2.1-0  rmarkdown_2.25    tools_4.3.2       pkgconfig_2.0.3  
    ## [37] htmltools_0.5.7

<div id="refs" class="references csl-bib-body hanging-indent"
entry-spacing="0">

<div id="ref-gdsc_genomics_2024" class="csl-entry">

Alipour, Samira. 2024. “Genomics of Drug Sensitivity in Cancer (GDSC).”
<https://www.kaggle.com/datasets/samiraalipour/genomics-of-drug-sensitivity-in-cancer-gdsc/data>.

</div>

<div id="ref-lubridate" class="csl-entry">

Grolemund, Garrett, and Hadley Wickham. 2011. “Dates and Times Made Easy
with <span class="nocase">lubridate</span>.” *Journal of Statistical
Software* 40 (3): 1–25. <https://www.jstatsoft.org/v40/i03/>.

</div>

<div id="ref-tibble" class="csl-entry">

Müller, Kirill, and Hadley Wickham. 2023. *Tibble: Simple Data Frames*.
<https://CRAN.R-project.org/package=tibble>.

</div>

<div id="ref-R-base" class="csl-entry">

R Core Team. 2024. *R: A Language and Environment for Statistical
Computing*. Vienna, Austria: R Foundation for Statistical Computing.
<https://www.R-project.org/>.

</div>

<div id="ref-stringr" class="csl-entry">

Wickham, Hadley. 2023. *Stringr: Simple, Consistent Wrappers for Common
String Operations*. <https://CRAN.R-project.org/package=stringr>.

</div>

<div id="ref-purrr" class="csl-entry">

Wickham, Hadley, and Lionel Henry. 2023. *Purrr: Functional Programming
Tools*. <https://CRAN.R-project.org/package=purrr>.

</div>

<div id="ref-tidyr" class="csl-entry">

Wickham, Hadley, Davis Vaughan, and Maximilian Girlich. 2024. *Tidyr:
Tidy Messy Data*. <https://CRAN.R-project.org/package=tidyr>.

</div>

</div>
