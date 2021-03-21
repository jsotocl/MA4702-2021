Página complementaria curso MA4702.
Esta página se actualizará con la información necesaria para los laboratorios del curso.

Instalación de software
1. Instalar Julia
(usar versión 1.54 o superior)

Instalar Julia. En la misma página están las instrucciones para añadir Julia a la variable de entorno PATH para así poder llamar julia mediante la terminal a través del comando julia.

Puede trabajar directamente en la linea de comandos o a través de un ambiente de desarrollo (IDE). Para trabajar de manera individual un buen IDE es JUNO Juno, editor de código construido sobre ATOM. Puede usar otros ambientes si asi lo desea.

En los laboratorios usaremos además el ambiente Jupyter notebook.

2. Instalar Jupyter Notebook
Julia cuenta con IJulia, un paquete que permite utilizar el entorno interactivo de Jupyter notebook.

Primero debe instalar el paqueta IJulia ejecutando los siguientes comandos (solo la primera vez que lo usa)

Nota: Pkg es el gestor de paquetes de Julia, lo usaremos bastante para instalar nuevas funcionalidades.

julia>  import Pkg
julia>  Pkg.add("IJulia")
Para abrir Jupyter notebook en el navegador se debe desde la consola de Julia ejecutar los siguientes comandos:

julia>  using IJulia
julia>  notebook()
3. Instalar Gurobi
Descargar gurobi v9.1.1 o superior en el siguiente link. Las instrucciones para instalarlo en su sistema operativo están en el mismo link en el archivo README. Para facilitar los siguientes pasos, es conveniente que instale Gurobi en un directorio con nombre sencillo (directo en la raíz, Gurobi911 por ejemplo).

https://www.gurobi.com/downloads/gurobi-software/

Solicitar la licencia aquí (debe registrarse como estudiante de la Universidad)

https://www.gurobi.com/downloads/end-user-license-agreement-academic/

Para activar la licencia desde un computador con gurobi instalado debe ejecutar un comando (grbgetkey numero-licencia) desde la linea de comandos y conectado a internet (no requiere VPN). Las instrucciones de activación están en esta url:

https://www.gurobi.com/downloads/free-academic-license/

4. Instalar API de Gurobi en Julia
Una vez que tenga Gurobi instalado, necesitamos que Julia se pueda comunicar con Gurobi. Para instalar la API de Gurobi de Julia debe fijar la variable de entorno con el directorio en el que está instalado Gurobi y luego instalar los paquetes apropiados (para más detalles, puede ir a https://github.com/JuliaOpt/Gurobi.jl)

# On Windows, this might be
ENV["GUROBI_HOME"] = "C:\\Program Files\\gurobi910\\win64"
# ... or perhaps ...
ENV["GUROBI_HOME"] = "C:\\gurobi910\\win64"
import Pkg
Pkg.add("Gurobi")
Pkg.build("Gurobi")

# On Mac, this might be
ENV["GUROBI_HOME"] = "/Library/gurobi910/mac64"
import Pkg
Pkg.add("Gurobi")
Pkg.build("Gurobi")
Para instalar JuMP:

Pkg.add(PackageSpec(url="https://github.com/JuliaOpt/JuMP.jl/", rev="master"))
Nota:
Los paquetes se pueden instalar desde Jupyter o desde la terminal de Julia, si la instalación falla en Jupyter se sugiere instalar desde la terminal de julia, al entrar a la terminal escribir ] para entrar el modo gestor de paquetes, para salir del modo apretar backspace, por ejemplo:

#instalar
pkg> add GLPK #primera opción
pkg> build GLPK #segunda opción si no funciona el primero
#apretar backspace
julia> using GLPK #importar paquete
Alternativamente:

julia>  using Pkg
julia>  Pkg.add("GLPK")  #primera opción
julia>  Pkg.build("GLPK") #segunda opción si no funciona el primero
4. Documentación y guías
Introducción a Julia
Documentación Julia
Documentación Gurobi
Documentación JuMP
