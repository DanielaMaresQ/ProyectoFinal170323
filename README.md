INSTALACIÓN: 
Los paquetes que se necesitan instalar para poder reproducir el código son GEOparse, Pandas y Matplotlib.pyplot.
CORRIDA:
Este código realiza un análisis de expresión diferencial usando muestras de cáncer de mama y muestras normales de epitelio de mama a través del uso de la biblioteca de Python GEOparse. El análisis se enfoca en el dataset de GEO GSE15852. El cuál se analizó en GEO usando el análisis de GEO2R, se definieron los grupos a analizar, es de mi interés estudiar el subtipo de cáncer de mama ductal infiltrante, por lo que sólo seleccioné 35 muestras de la expresión de genes en pacientes con cancer de mama de tipo ductal infiltrante y 35 muestras de epitelio de mama de pacientes sanos. Se hizo el análisis de expresión diferencial. Usé Python para yo obtener mis propios análisis y gráficas específicos de este subgrupo. 
El resultado es la cargar archivos de entrada como Topdifferentiallyexpressedgenes.csv, infiltratingductalcarcinomavsnormalpadjmenor0.05forVolcanoplot; infiltratingductalcarcinomvsnormal_limma_padvmenor0.05forVennDiagram, Genes.mayor.adj.p.val.GO.csv, Genes.menor.adj.p.val.GO.csv.
Generación de archivos de datos (salida) como: phenotype_data, top_GDE. archivos de gráficas (salida): graficadeVolcan_GED.png, DiagramadeVenn_GDE.png, grafica_funciones_genessobreexpresados_GO, grafica_funciones_genessubexpresados_GO. Para ejecutar este código, se siguen los siguientes pasos:
Clona el repositorio de GitHub DanielaMaresQ/ProyectoFinal170323.
Abre una terminal y navega al directorio del repositorio. Crea un entorno virtual de Python para instalar las dependencias necesarias. Se puede usar virtualenv para ello. En la terminal, se escribe: virtualenv env. Esto creará un nuevo entorno virtual de Python en el directorio actual.Se activa el entorno virtual, escribiendo en la terminal:  source env/bin/actívate. Para instalar las dependencias necesarias se debe de escribir en el bash, pip install -r requirements.txt. Esto instalará los paquetes que se usaron como GEOparse, pandas y matplotlib. Se corre el código que se proporcionó en el archivo llamado ProyectoFinalWBDS_150323 (1).ipynb.
Los archivos de entrada y de salida se encuentran en el repositorio de GitHub DanielaMaresQ/ProyectoFinal170323.



PROBLEMA A RESOLVER:
El problema con los subtipos de cáncer es que cada tipo de cáncer puede tener diferentes subtipos, lo que dificulta el diagnóstico y el tratamiento. Los subtipos de cáncer se diferencian por su origen celular, su comportamiento y su respuesta al tratamiento, lo que significa que pueden requerir enfoques de tratamiento diferentes.
Además, algunos subtipos de cáncer pueden ser más agresivos y propagarse más rápidamente que otros, lo que puede dificultar aún más el tratamiento y la curación del cáncer de mama. Por lo tanto, es importante que los médicos determinen el subtipo específico de cáncer que un paciente tiene para poder desarrollar un plan de tratamiento adecuado y efectivo. Se decidió realizar un análisis de expresión diferencial para el subtipo de cáncer de mama ductal infiltrante. 

DESCRIBIR:
El análisis se enfoca en el dataset de GEO GSE15852. El cuál se analizó en GEO usando el análisis de GEO2R, el cuál está formado por 43 muestras de genes expresados en pacientes con diferentes tipos de cáncer de mama y 43 muestras de pacientes sanos. Se definieron los grupos a analizar, es de mi interés estudiar el subtipo de cáncer de mama ductal infiltrante, por lo que sólo seleccioné 35 muestras de la expresión de genes en pacientes con cancer de mama de tipo ductal infiltrante y 35 muestras de epitelio de mama de pacientes sanos. El análisis de expresión diferencial de genes del set de datos en mención es importante porque puede ayudar a identificar qué genes están involucrados en el desarrollo del cáncer de mama y cómo estos genes pueden estar regulando la proliferación celular y la invasión.



1.	Se descargaron los datos de GEO del dataset GSE15852, usando el paquete GEOparse
2.	Para cargar los datos a Python, se importó la librería de pandas y de matplotlib.
3.	Se cargaron los datos del dataset GSE15852,
4.	Se vio el metadato en donde se puede leer la descripción de este dataset, que consta de la expresión génica de 43 pacientes con cáncer de mama de diferentes tipos y 43 pacientes sanos. Además cuenta con el archivo phenotype_data
5.	Se observó el archivo phenotype_data usando el comando print. 
6.	Se navegó por el metadato viendo los directorios disponibles, usando dir.
7.	Para ver la información en el diccionario gsm se usó un for y se imprimió.
8.	Se revisó con qué claves cuenta el metadato usando for gsm_name, gsm in gse.gsms.items() y se imprimieron. 
9.	Se quiso conocer qué claves están disponibles en el archivo de phenotype_data.
10.	Se investigó en que ruta se van a descargar los archivos que se produzcan
11.	Se descargó el archivo 1phenotype_data.csv
12.	Se vieron los encabezados del archivo 1phenotype_data.csv
13.	Se contó con cuantas filas cuenta el archivo usando len
14.	Se conoció el tamaño de la tabla usando shape
15.	Se le pidió al programa que nos retorne los primeros GEO accession y los últimos GEO accession del archivo llamado df
16.	Para realizar, la continuación del estudio de expresión diferencial usando la herramienta disponible en GEO, llamada GEO2R https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE15852 se definió que sólo se va a trabajar con 35 muestras de la expresión de genes en pacientes con cancer de mama de tipo ductal infiltrante y 35 muestras de epitelio de mama de pacientes sanos y de aquí se obtuvo la matriz llamada Topdifferentiallyexpressedgenes.csv, que se usó como archivo de entrada en en Python.
17.	Se aplicó sort:values, sorted_asc y sorted_desc para obtener el nombre de los 10 genes con el adj.P.Val más pequeño y los 10 genes con el adj.P.Val más grande de la columna Gene.title.
18.	Se imprimieron los resultados
19.	Se generó un archivo llamado “top_GDE que es el archivo de salida que contiene los resultados tanto para los 10 genes con el adj.P.Value más pequeño como para los 10 genes con el adj.P.Value más grande, agregando en una columna sus valores de adj.P.Value.
20.	Se hizo un gráfico de gráfico de volcan del archivo que se llama infiltrating ductal carcinoma vs normal, padjmenor0.05forVolcanoplot usando para el eje de las x la columna que se llama log2(fold change) y como eje de las y la columna que se llama -log10(Pvalue). El archivo de salida se llama graficadeVolcan_GED.png
21.	Se realizó un diagrama de Venn usando como archivo de entrada infiltratingductalcarcinomvsnormal_limma_padvmenor0.05forVennDiagram.csv y el archivo de salida que se generó se llama DiagramadeVenn_GDE.png
22.	Se hizo la gráfica de barras dinámica con las funciones de GO para los genes sobreexpresados, se cargó el archivo de entrada llamado "Genes.menor.adj.p.val.GO.csv" se usó en el eje de las y, las columnas llamadas "adj.P.Val" ,"GO.Function","GO.Process","GO.Component", en el eje de las x la columna llamada "Gene.symbol"  Se generó un archivo de salida llamado grafica_funciones_genessobreexpresados_GO.png.
23.	Se realizó la gráfica de barras dinámica con las funciones de GO para los genes subexpresados, se ingresó el archivo de entrada llamado "Genes.menor.adj.p.val.GO.csv" se usó en el eje de las y, las columnas llamadas "adj.P.Val" ,"GO.Function","GO.Process","GO.Component", en el eje de las x la columna llamada "Gene.symbol". Se obtuvo el archivo de salida llamado grafica_funciones_genessubexpresados_GO.png.
24.	Se agregó la licencia de tipo de creative commons. 
Los archivos de entrada y de salida se encuentran en el repositorio de GitHub DanielaMaresQ/ProyectoFinal170323.

SOFTWARE Y BASES DE DATOS ESPECÍFICOS DEL ÁREA:
Se trabajó con Juypter notebook debido a que me pareció más fácil de usar que Google colab, además es compatible con muchos lenguajes de programación, y se puede trabajar con una variedad de herramientas y bibliotecas. Jupyter Notebook puede funcionar sin conexión a internet. Se pueden personalizar las bibliotecas. 
Se prefirió usar la base de datos de Gene Expression Onmibus en vez de la del Atlas del Cáncer debido a que GEO tiene mayor cantidad de datos, así como mayor diversidad de muestras de diferentes tipos de células, tejidos y organismos. GEO tiene tiene la herramienta de GEO2R la cuál me permitió hacer el análisis de expresión diferencial desde la plataforma.  
https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE15852
RESUME LOS RESULTADOS.
El set de datos GSE15852 está compuesto por los siguientes archivos. 
Metadata: contiene los metadatos asociados con el archivo GEO. Puedes explorar este atributo para ver información como el título del estudio, la descripción, el tipo de experimento y otros detalles importantes.

Phenotype_data: contiene información detallada sobre cada muestra en el archivo, incluyendo su ID, el tratamiento al que se sometió y otros detalles relevantes.

Gsms: contiene información detallada sobre cada muestra en el archivo, incluyendo su ID, las condiciones experimentales y otros detalles relevantes.

Gpls: contiene información sobre las sondas utilizadas en el experimento.
–
Se obtuvo del número de acceso
Accession: PRJNA116827 ID: 116827
–
Se conoció con los diccionarios que cuenta el data set GSE15852
DICCIONARIOS
GSM398074
GSM398075
GSM398076
GSM398077
GSM398078
GSM398079
GSM398080
GSM398081
GSM398082
GSM398083
GSM398084
GSM398085
GSM398086
GSM398087
GSM398088
GSM398089
GSM398090
GSM398091
GSM398092
GSM398093
GSM398094
GSM398095
GSM398096
GSM398097
GSM398098
GSM398099
GSM398100
GSM398101
GSM398102
GSM398103
GSM398104
GSM398105
GSM398106
GSM398107
GSM398108
GSM398109
GSM398110
GSM398111
GSM398112
GSM398113
GSM398114
GSM398115
GSM398116
GSM398117
GSM398118
GSM398119
GSM398120
GSM398121
GSM398122
GSM398123
GSM398124
GSM398125
GSM398126
GSM398127
GSM398128
GSM398129
GSM398130
GSM398131
GSM398132
GSM398133
GSM398134
GSM398135
GSM398136
GSM398137
GSM398138
GSM398139
GSM398140
GSM398141
GSM398142
GSM398143
GSM398144
GSM398145
GSM398146
GSM398147
GSM398148
GSM398149
GSM398150
GSM398151
GSM398152
GSM398153
GSM398154
GSM398155
GSM398156
GSM398157
GSM398158
GSM398159

—
Se conoció las claves de datos que se encuentran en el diccionario GSM398074.
Muestra:  GSM398074
Claves de metadatos:  dict_keys(['title', 'geo_accession', 'status', 'submission_date', 'last_update_date', 'type', 'channel_count', 'source_name_ch1', 'organism_ch1', 'taxid_ch1', 'characteristics_ch1', 'treatment_protocol_ch1', 'growth_protocol_ch1', 'molecule_ch1', 'extract_protocol_ch1', 'label_ch1', 'label_protocol_ch1', 'hyb_protocol', 'scan_protocol', 'description', 'data_processing', 'platform_id', 'contact_name', 'contact_email', 'contact_phone', 'contact_laboratory', 'contact_department', 'contact_institute', 'contact_address', 'contact_city', 'contact_state', 'contact_zip/postal_code', 'contact_country', 'supplementary_file', 'series_id', 'data_row_count'])

–
El archivo de “1phenotype_data.csv” cuenta con 86 filas. 
El tamaño de la tabla son 86 filas y 41 columnas: (86, 41)

Los primeros GEO Accession del dataset GSE15852 son:
0    GSM398074
1    GSM398075
2    GSM398076
3    GSM398077
4    GSM398078
Name: geo_accession, dtype: object
Los últimos GEO Accession del data set GSE15852 son:
81    GSM398155
82    GSM398156
83    GSM398157
84    GSM398158
85    GSM398159
Análisis de genes expresados diferencialmente. 

Genes expresados diferencialmente en cáncer de mama tipo ductal infiltrante.

Gene.title	adj.P.Val
CD24 molecule	1.45E-11
protein phosphatase 1 regulatory inhibitor subunit 1A	4.72E-11
keratin 19	4.72E-11
epithelial cell adhesion molecule	4.72E-11
keratin 18	4.03E-10
regulator of G-protein signaling 1	4.03E-10
syndecan 1	6.37E-10
retinol binding protein 4	6.37E-10
angiopoietin like 4	6.37E-10
phosphodiesterase 3B	1.52E-09
ADAM metallopeptidase with thrombospondin type 1 motif 12	1
NOP2/Sun RNA methyltransferase family member 5 pseudogene 1	1
zinc finger protein 235	1
integrin subunit beta 3	1
widely interspaced zinc finger motifs	1
huntingtin interacting protein 1	1
G protein-coupled receptor 161	1
adenylate kinase 1	1
acylglycerol kinase	1
HemK methyltransferase family member 1	1










Gráfica de Volcán
 
Se muestran los 250 genes, algunos están sobreexpresión en el data set así como otros se encuentran subexpresados-

Diagrama de Venn

 Este código creará un diagrama de Venn de tres conjuntos que muestra la intersección de los genes en todos los conjuntos, los genes que están sobre regulados y los genes que están sub regulados . Los nombres de los conjuntos se especifican como una tupla en el tercer argumento de la función venn3- 

Gene Onthology del top de genes con sobreexpresión
Con la intención de conocer algunas de las funciones que realizan el top de genes con sobreexpresión se realizó una gráfica de barras y ontología de genes. 
La barra de gráficas aplicadas: permite visualizar de manera clara la contribución de cada función GO al valor de "adj.P.Val" para cada gen..

 
Funciones:

Gen	GO.Function	GO.Process	GO.Component
CD24	protein binding///protein kinase binding///protein tyrosine kinase activator activity///signal transducer activity	B cell receptor transport into membrane raft///T cell costimulation///Wnt signaling pathway///cell activation///cell migration///chemokine receptor transport out of membrane raft///cholesterol homeostasis///glomerular parietal epithelial cell differentiation///glomerular visceral epithelial cell differentiation///immune response-regulating cell surface receptor signaling pathway///intrinsic apoptotic signaling pathway///negative regulation of transforming growth factor beta3 production///positive regulation of MAP kinase activity///positive regulation of activated T cell proliferation///positive regulation of cytosolic calcium ion concentration///positive regulation of nephron tubule epithelial cell differentiation///positive regulation of protein tyrosine kinase activity///regulation of MAPK cascade///regulation of cytokine-mediated signaling pathway///regulation of epithelial cell differentiation///regulation of phosphorylation///respiratory burst///response to estrogen///response to hypoxia///response to molecule of bacterial origin///single organismal cell-cell adhesion	anchored component of external side of plasma membrane///cell surface///intracellular///membrane///membrane raft
PPP1R1A	protein binding///protein serine/threonine phosphatase inhibitor activity	glycogen metabolic process///intracellular signal transduction///negative regulation of protein kinase activity	cytoplasm///extracellular space
KRT19	protein binding///protein complex binding///structural constituent of cytoskeleton///structural constituent of muscle	Notch signaling pathway///cell differentiation involved in embryonic placenta development///response to estrogen///sarcomere organization///viral process	Z disc///cell periphery///costamere///dystrophin-associated glycoprotein complex///extracellular exosome///intermediate filament///plasma membrane///sarcolemma///terminal web
EPCAM	cadherin binding involved in cell-cell adhesion///protein binding///protein complex binding	cell-cell adhesion///negative regulation of apoptotic process///negative regulation of cell-cell adhesion mediated by cadherin///positive regulation of cell motility///positive regulation of cell proliferation///positive regulation of stem cell proliferation///positive regulation of transcription from RNA polymerase II promoter///signal transduction involved in regulation of gene expression///stem cell differentiation///ureteric bud development	apical plasma membrane///basolateral plasma membrane///bicellular tight junction///cell surface///extracellular exosome///integral component of plasma membrane///lateral plasma membrane///plasma membrane
KRT18	cadherin binding involved in cell-cell adhesion///poly(A) RNA binding///protein binding///scaffold protein binding///structural molecule activity	Golgi to plasma membrane CFTR protein transport///anatomical structure morphogenesis///cell cycle///cell-cell adhesion///extrinsic apoptotic signaling pathway///hepatocyte apoptotic process///intermediate filament cytoskeleton organization///negative regulation of apoptotic process///tumor necrosis factor-mediated signaling pathway///viral process	cell periphery///cell-cell adherens junction///centriolar satellite///cytoplasm///extracellular exosome///intermediate filament///keratin filament///microtubule organizing center///nucleolus///perinuclear region of cytoplasm
RGS1	G-protein alpha-subunit binding///GTPase activator activity///calmodulin binding	G-protein coupled receptor signaling pathway///adenylate cyclase-inhibiting G-protein coupled receptor signaling pathway///immune response///leukotriene signaling pathway///negative regulation of signal transduction///positive regulation of GTPase activity///regulation of G-protein coupled receptor protein signaling pathway///signal transduction	cytosol///extrinsic component of cytoplasmic side of plasma membrane///plasma membrane
SDC1	glycoprotein binding///protein C-terminus binding///protein binding	Sertoli cell development///canonical Wnt signaling pathway///cell migration///glycosaminoglycan biosynthetic process///glycosaminoglycan catabolic process///glycosaminoglycan metabolic process///inflammatory response///lipoprotein metabolic process///myoblast development///odontogenesis///positive regulation of exosomal secretion///positive regulation of extracellular exosome assembly///response to cAMP///response to calcium ion///response to glucocorticoid///response to hydrogen peroxide///response to toxic substance///retinoid metabolic process///striated muscle cell development///ureteric bud development///wound healing	Golgi lumen///cell surface///cytoplasm///external side of plasma membrane///extracellular exosome///focal adhesion///integral component of plasma membrane///lysosomal lumen///plasma membrane///protein complex
RBP4	protein binding///protein heterodimerization activity///retinal binding///retinol binding///retinol transporter activity	cardiac muscle tissue development///embryonic organ morphogenesis///embryonic retina morphogenesis in camera-type eye///embryonic skeletal system development///eye development///eye development///female genitalia morphogenesis///gluconeogenesis///gluconeogenesis///glucose homeostasis///heart development///heart trabecula formation///lung development///maintenance of gastrointestinal epithelium///negative regulation of cardiac muscle cell proliferation///positive regulation of immunoglobulin secretion///positive regulation of insulin secretion///response to ethanol///response to retinoic acid///retinoid metabolic process///retinol metabolic process///retinol transport///urinary bladder development///uterus development///vagina development///visual perception	cytosol///extracellular exosome///extracellular region///extracellular space///extracellular space///protein complex
ANGPTL4	enzyme inhibitor activity///identical protein binding///protein binding	angiogenesis///cell differentiation///negative regulation of apoptotic process///negative regulation of endothelial cell apoptotic process///negative regulation of lipoprotein lipase activity///positive regulation of angiogenesis///protein homooligomerization///response to hypoxia///triglyceride homeostasis	blood microparticle///extracellular region///extracellular region///extracellular space///proteinaceous extracellular matrix
TACSTD2	protein binding///receptor activity	cell proliferation///cell surface receptor signaling pathway///cell-cell adhesion///negative regulation of branching involved in ureteric bud morphogenesis///negative regulation of cell motility///negative regulation of epithelial cell migration///negative regulation of ruffle assembly///negative regulation of stress fiber assembly///negative regulation of substrate adhesion-dependent cell spreading///positive regulation of stem cell differentiation///regulation of epithelial cell proliferation///ureteric bud morphogenesis///visual perception	basal plasma membrane///cytosol///extracellular exosome///extracellular space///integral component of plasma membrane///lateral plasma membrane///membrane///nucleus


Gene onthology del top de genes subexpresados y sus funciones
Con la intención de conocer algunas de las funciones que realizan el top de genes con subexpresión  se realizó una gráfica de barras y ontología de genes. 
La barra de gráficas aplicadas:Esta opción permite visualizar de manera clara la contribución de cada función GO al valor de "adj.P.Val" para cada gen..
 




Funciones

Gen	GO.Function	GO.Process	GO.Component
TBXA2R	guanyl-nucleotide exchange factor activity///protein binding///thromboxane A2 receptor activity	G-protein coupled receptor signaling pathway///adenylate cyclase-activating G-protein coupled receptor signaling pathway///inflammatory response///positive regulation of GTPase activity///positive regulation of angiogenesis///positive regulation of blood pressure///positive regulation of cytosolic calcium ion concentration///positive regulation of smooth muscle contraction///positive regulation of vasoconstriction///response to drug///response to lipopolysaccharide///response to nutrient///second-messenger-mediated signaling///thromboxane A2 signaling pathway	acrosomal vesicle///cytosol///integral component of plasma membrane///plasma membrane
SMOX	N1-acetylspermine:oxygen oxidoreductase (N1-acetylspermidine-forming) activity///norspermine:oxygen oxidoreductase activity///polyamine oxidase activity///spermine:oxygen oxidoreductase (spermidine-forming) activity	oxidation-reduction process///polyamine biosynthetic process///polyamine catabolic process///spermine catabolic process	cytoplasm///cytosol///nucleus
BRD2	chromatin binding///lysine-acetylated histone binding///protein binding	covalent chromatin modification///nucleosome assembly///regulation of transcription from RNA polymerase II promoter///spermatogenesis///transcription, DNA-templated	cytoplasm///nucleus
RING1	chromatin binding///ligase activity///protein binding///ubiquitin-protein transferase activator activity///zinc ion binding	anterior/posterior pattern specification///camera-type eye morphogenesis///histone H2A monoubiquitination///negative regulation of transcription, DNA-templated///protein sumoylation///regulation of catalytic activity///transcription, DNA-templated	PRC1 complex///PcG protein complex///cytoplasm///nuclear speck///nucleoplasm///nucleoplasm///nucleus///sex chromatin
GPS1	GTPase inhibitor activity///protein binding	COP9 signalosome assembly///JNK cascade///cell cycle///cullin deneddylation///inactivation of MAPK activity///negative regulation of GTPase activity///nucleotide-excision repair, DNA damage recognition///transcription-coupled nucleotide-excision repair	COP9 signalosome///cytoplasm///nucleoplasm
PKD1P1			
PEX10	protein binding///zinc ion binding	peroxisome organization///protein import into peroxisome matrix	integral component of peroxisomal membrane///peroxisome
MAN1A2	calcium ion binding///mannosyl-oligosaccharide 1,2-alpha-mannosidase activity	Golgi apparatus mannose trimming///N-glycan processing///lung alveolus development///respiratory gaseous exchange	Golgi apparatus///Golgi membrane///Golgi membrane///endoplasmic reticulum///extracellular exosome///integral component of membrane///membrane
FGB	contributes_to cell adhesion molecule binding///chaperone binding///protein binding///protein binding, bridging///contributes_to receptor binding///structural molecule activity	adaptive immune response///blood coagulation///blood coagulation, fibrin clot formation///cell-matrix adhesion///cellular protein complex assembly///cellular response to interleukin-1///cellular response to leptin stimulus///extracellular matrix organization///fibrinolysis///induction of bacterial agglutination///innate immune response///negative regulation of endothelial cell apoptotic process///negative regulation of extrinsic apoptotic signaling pathway via death domain receptors///plasminogen activation///platelet aggregation///platelet degranulation///positive regulation of ERK1 and ERK2 cascade///positive regulation of exocytosis///positive regulation of heterotypic cell-cell adhesion///positive regulation of peptide hormone secretion///positive regulation of protein secretion///positive regulation of substrate adhesion-dependent cell spreading///positive regulation of vasoconstriction///protein polymerization///response to calcium ion///signal transduction	blood microparticle///cell cortex///cell surface///external side of plasma membrane///extracellular exosome///extracellular region///extracellular region///extracellular space///extracellular vesicle///fibrinogen complex///plasma membrane///platelet alpha granule///platelet alpha granule lumen
ADAMTS12	metalloendopeptidase activity///protein binding///zinc ion binding	cell migration///cell-matrix adhesion///cellular response to BMP stimulus///cellular response to interleukin-1///cellular response to tumor necrosis factor///negative regulation of cellular response to hepatocyte growth factor stimulus///negative regulation of cellular response to vascular endothelial growth factor stimulus///negative regulation of chondrocyte differentiation///negative regulation of hepatocyte growth factor receptor signaling pathway///proteoglycan catabolic process///proteolysis involved in cellular protein catabolic process///proteolysis involved in cellular protein catabolic process///regulation of endothelial tube morphogenesis///regulation of inflammatory response	extracellular matrix///proteinaceous extracellular matrix
Discusión 

El adj.P.Val (valor de p ajustado) es una medida estadística que se utiliza para evaluar la significancia de la diferencia en la expresión de genes entre dos grupos (por ejemplo, cáncer y normal). Los valores de p ajustados son una corrección de los valores de p crudos (no ajustados) que tienen en cuenta el número de pruebas realizadas y reducen el riesgo de obtener falsos positivos.
En un análisis de expresión diferencial, los 10 mayores adj.P.Val indican los 10 genes que tienen una mayor probabilidad de ser significativamente diferentes entre los grupos de cáncer y normal. Por otro lado, los 10 menores adj.P.Val indican los 10 genes que tienen una menor probabilidad de ser significativamente diferentes entre los grupos.
En general, los genes con valores de p ajustados más bajos (valores más pequeños) se consideran más significativos y relevantes en el análisis de expresión diferencial. Por lo tanto, los genes con los valores de p ajustados más bajos se consideran más importantes para comprender las diferencias en la expresión génica entre los grupos de cáncer y normal. Sin embargo, es importante tener en cuenta que la interpretación de los resultados de expresión diferencial no debe basarse únicamente en los valores de p ajustados, sino que debe considerarse en conjunto con otros factores biológicos y experimentales relevantes.

Algunos de los genes con sobreexpresión del análisis de expresión diferencial se ha reportado la siguiente información. 

CD24: es una glicoproteína transmembrana que se expresa en la superficie de muchas células, incluyendo células madre hematopoyéticas, células B y células epiteliales. En el cáncer de mama, se ha demostrado que CD24 está sobreexpresado en varios subtipos, incluyendo el carcinoma ductal infiltrante. Se cree que CD24 está involucrado en la proliferación celular, la invasión y la migración en el cáncer de mama. Además, se ha propuesto que CD24 puede ser un objetivo terapéutico en el tratamiento del cáncer de mama, ya que su sobreexpresión se ha asociado con una peor supervivencia, se ha propuesto como un marcador pronóstico para cáncer de mama (Kristiansen et al., 2023)
PPP1R1A: también conocida como proteína fosfatasa 1 reguladora subunidad 1A, es una proteína que actúa como modulador de la fosfatasa de proteína 1 (PP1), una enzima implicada en la regulación de diversas funciones celulares como la señalización intracelular, la división celular y la apoptosis. En relación con el cáncer de mama, estudios han demostrado que PPP1R1A actúa como un supresor tumoral en las células mamarias, inhibiendo la proliferación y migración celular y promoviendo la apoptosis. Además, se ha encontrado que la expresión de PPP1R1A está disminuida en los tumores de mama, en particular en el subtipo de carcinoma ductal infiltrante, lo que sugiere que puede desempeñar un papel importante en la progresión del cáncer de mama y en la respuesta al tratamiento
KRT19: es un gen que codifica para la proteína citoqueratina 19, que es una proteína filamental de tipo I que forma parte del citoesqueleto de las células epiteliales. En el carcinoma ductal infiltrante de mama, KRT19 se ha encontrado sobreexpresado en comparación con el tejido mamario normal. Se ha demostrado que KRT19 puede ser utilizado como un marcador para identificar células tumorales circulantes en la sangre de pacientes con cáncer de mama, lo que puede tener implicaciones en la detección temprana y el seguimiento de la enfermedad. Además, se ha sugerido que KRT19 podría estar involucrado en la progresión tumoral y en la adquisición de características invasivas por las células tumorales.
Regenerate response


Algunos de los genes con subexpresión del análisis de expresión diferencial se ha reportado la siguiente información. 

TBXA2R:es el receptor para la tromboxano A2, que es una molécula producida por las plaquetas y que está involucrada en la agregación plaquetaria y la vasoconstricción. Por lo tanto, el TBXA2R es importante en la función de las células sanguíneas y en la regulación de la circulación sanguínea. Además, el TBXA2R también se ha encontrado en otros tipos de células, como células musculares lisas, células endoteliales y células de cáncer. En estas células, el TBXA2R también puede estar involucrado en la regulación de la proliferación celular, la migración y la apoptosis. Sin embargo, la investigación sobre la función del TBXA2R en estos otros tipos de células aún es limitada y se necesitan más estudios para comprender completamente su papel en el funcionamiento celular
SMOX: SMOX es el gen que codifica la enzima llamada spermina oxidasa, que está involucrada en la oxidación de la poliamina spermina a espermidina. Las poliaminas son moléculas importantes que desempeñan un papel crucial en la división celular, la diferenciación y la proliferación celular. SMOX ha sido implicado en varias enfermedades, incluyendo el cáncer. En el carcinoma ductal infiltrante de mama, la expresión de SMOX ha sido encontrada estar aumentada en comparación con el tejido mamario normal, lo que sugiere que puede desempeñar un papel en el desarrollo y progresión del cáncer de mama. Sin embargo, se necesitan más estudios para comprender completamente el papel exacto de SMOX en el carcinoma ductal infiltrante de mama.
BRD2: es un gen que codifica una proteína que pertenece a la familia de las bromodominas. Las bromodominas son dominios de unión a acetil- lisina y están presentes en proteínas que regulan la transcripción génica. Se ha demostrado que BRD2 es un factor de transcripción que se une a histonas acetiladas y actúa como un regulador positivo de la transcripción de ciertos genes. Además, se ha implicado a BRD2 en la regulación del ciclo celular, la apoptosis y la diferenciación celular. Se ha observado que la expresión de BRD2 está aumentada en algunos tipos de cáncer, incluido el carcinoma ductal infiltrante de mama, y se ha propuesto como un posible objetivo terapéutico para el tratamiento del cáncer.

Conclusión
El análisis de expresión diferencial nos permitió identificar 20 genes clave en el subtipo de cáncer de mama ductal infiltrante. Diez se encuentran sobreexpresados como CD24, PPP1R1A, KRT19, EPCAM, KRT18, RGS1, SDC1, RBP4, ANGPTL4, TACSTD2. Diez se encuentran subexpresados como TBXA2R, SMOX, BRD2, RING1, GPS1, PKD1P1, PEX10, MAN1A2, FGB, ADAMTS12. Algunos de estos genes ya hay evidencia científica que desempeñan un rol importante en el cáncer de mama como CD24, sin embargo, se necesitan más estudios para poder usarlos cómo marcadores específicos para el subtipo ductal infiltrante. Los cambios en la expresión génica se relacionan con diferentes procesos biológicos, como el desarrollo, la diferenciación celular, la respuesta inmune, la enfermedad y la terapia, por lo que el desarrollo de estudios subsecuentes en esta área, podría proporcionar información valiosa para el desarrollo de nuevas terapias dirigidas a los genes específicos involucrados.



