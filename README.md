# hadoop

hdfs namenode -format <— Formatea el sistema de archivos
hstart <— Inicializa hadoop
hstop <— Detiene hadoop

Agreguar al .bash_profile: 
export JAVA_HOME="$(/usr/libexec/java_home)"
export PATH=$JAVA_HOME/bin:$PATH
export HADOOP_CLASSPATH=$JAVA_HOME/lib/tools.jar

Recompilar .bash_profile:
source .bash_profile 

Compile WordCount.java and create a jar:
hadoop com.sun.tools.javac.Main WordCount.java <-- Compila el archivo WordCount
jar cf wc.jar WordCount*.class  <-- Crea el .jar
had fs -mkdir /input/
cd input/
hadoop fs -put file01 /input
hadoop fs -put file02 /input
hadoop jar wc.jar WordCount /input /output <-- Ejecuta el programa y envía la salidad al directorio /output
hdfs dfs -cat /output/part-r-0000  <-- Imprime en pantalla la salida del programa WordCount

hdfs dfs -rmr /output     <-- Instrucción para borrar directorios del sistema de archivos de hadoop.



Programa que determina la calidad del aire en España.

$hadoop com.sun.tools.javac.Main AirQualityManager.java
$jar cf ca.jar AirQualityManager*.class
$hadoop fs -mkdir /calidad
$hadoop fs -put calidad_del_aire_cyl_1997_2013.csv /calidad
$hadoop jar ca.jar AirQualityManager /calidad /ca_output
$hdfs dfs -cat /ca_output
$hdfs dfs -cat /ca_output/part-r-00000
