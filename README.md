
# Equipe Atena - IEEE Open 2021

Projeto desenvolvido para a competição da IEEE Open (edital 2020/2021) para a modalidade da **LARC** *(Latin American Robotics Competition)*. O time é composto de membros do **Núcleo de Robótica Móvel (RMA)** do **Grupo SEMEAR**.

Para executar este projeto, são necessárias as seguintes dependências:

 **1.** Ubuntu 20.04\
 **2.** Compilador C++ 17\
 **3.** CMake > 3.16.8\
 **4.** Python > 3.8\
 **5.** [CoppeliaSim 4.2.0. (rev. 6)](https://www.coppeliarobotics.com/)\
 **6.** Biblioteca *"xsltproc"*\
 **7.** Pacote Python *"xmlschema"*\
 **8.** [ROS Noetic Ninjemys](http://wiki.ros.org/noetic/)\
 **9.** [Plugin de inteface ROS para CoppeliaSim](https://github.com/CoppeliaRobotics/simExtROS)\
 **10.** OpenCV\
 **11.** Tesseract\
 **12.** Leptonica

 A seguir, estão descritos os processos de instalação de cada dependência. 

## 1. Ubuntu 20.04
A imagem do sistema operacional **Ubuntu 20.04** pode ser baixada [no site oficial](https://ubuntu.com/).  A instalação de um sistema operacional depende muito do *hardware* em questão e dos demais *softwares* (como outros sistemas operacionais) já instalados. Logo, não será coberto em detalhes neste documento.

Antes de realizar a instalação das demais dependências, recomenda-se atualizar todos os *softwares* do sistema através do comando a seguir.

```console
username@user-computer:~$ sudo apt update
```

## 2. Compilador C++ 17
A instalação do **Ubuntu 20.04** já inclui a instalação de um compilador C++, cuja versão foi suficiente para executar este projeto. De toda forma, se for necessário, pode-se instalar o compilador *gcc* com o comando a seguir.

```console
username@user-computer:~$ sudo apt install build-essential
```
## 3. CMake > 3.16.8
A instalação do **Ubuntu 20.04** já inclui a instalação da ferramenta *cmake*, cuja versão foi suficiente para executar este projeto. Caso necessário, pode-se realizar a instalação de uma versão mais recente utilizando o código fonte disponível [no site oficial](https://cmake.org/).

## 4. Python > 3.8
A instalação do **Ubuntu 20.04** já inclui a instalação do interpretador com versão maior que 3.8 para o **Python**. Caso a versão seja menor que aquela de requisito, recomenda-se a utilização da ferramenta **Pyenv**. Ela permite a utilização de diferentes versões Python simultaneamente em uma mesma máquina e pode ser configurada utilizando as intruções contidas no [repositório oficial](https://github.com/pyenv/pyenv).

## 5. CoppeliaSim 4.2.0. (rev. 6)
Para realizar o *download* do simulador CoppeliaSim, basta acessar [a página de *Downloads* no site oficial](https://www.coppeliarobotics.com/downloads). Certifique que o sistema operacional selecionado é o **Ubuntu 20.04** e faça o *download* da versão EDU. O simulador é gratuito para fins educacionais, como é o caso deste projeto. Após o *download*, copie o arquivo para um local adequado *(será necessário acessar os arquivos com grande frequência, então cuidado)* e extraia o arquivo baixado utilizando o comando a seguir.

```console
tar -xf CoppeliaSim_Edu_V4_2_0_Ubuntu20_04.tar.xz
```
Após a extração, entre na pasta que foi extraída utilizando o comando a seguir.
```console
cd CoppeliaSim_Edu_V4_2_0_Ubuntu20_04
```
Para abrir o simulador, basta executar o comando a seguir.
```console
./coppeliaSim.sh
```
Ao abrir o simulador, confira se a versão está de acordo com aquela necessária para executar este projeto.

## 6. Biblioteca *"xsltproc"*
Esta biblioteca é uma dependência do **9. Plugin de inteface ROS para CoppeliaSim**. Para instalá-la, basta executar o comando a seguir.

```console
username@user-computer:~$ sudo apt-get install xsltproc
```

## 7. Pacote Python *"xmlschema"*
Esta biblioteca é uma dependência do **9. Plugin de inteface ROS para CoppeliaSim**. Para instalá-la, basta executar o comando a seguir.

```console
username@user-computer:~$ pip3 install xmlschema
```
Caso o comando *pip3* não seja reconhecido, é necessário instalá-lo através do comando a seguir.

```console
username@user-computer:~$ sudo apt-get install pip3
```

## 8. ROS Noetic Ninjemys
**ROS** (*Robot Operating System*) é uma *framework* utilizada para o desenvolvimento de sistemas robóticos. Ela facilita muitos processos de paralelismo e modularização do sistema de um robô, sendo utilizada em pesquisas estado-da-arte e no mercado de trabalho. Para instalar, basta acessar [o tutorial de instalação oficial do ROS](http://wiki.ros.org/noetic/Installation/Ubuntu). Os passos descritos neste tutorial também estão descritos a seguir.

O primeiro passo é preparar o sistema para aceitar *softwares* proprietários do **ROS**.

```console
username@user-computer:~$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

Depois disso, é necessário setar as chaves com os comandos a seguir.
```console
username@user-computer:~$ sudo apt install curl
```
```console
username@user-computer:~$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
Para efetivamente realizar a instalação, execute os comandos a seguir.
```console
username@user-computer:~$ sudo apt update
```
```console
username@user-computer:~$ sudo apt install ros-noetic-desktop-full
```
O sistema **ROS** precisa definir algumas variáveis de ambiente toda vez que um terminal é executado. Para isso, basta atualizar o arquivo *~/.bashrc* executando os comandos a seguir. Alternativamente, pode-se abrir o arquivo em questão em um editor de texto e inserir o termo entre aspas duplas do primeiro comando abaixo.
 
```console
username@user-computer:~$ echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```
```console
username@user-computer:~$ source ~/.bashrc
```

Para executar pacotes **ROS**, algumas dependências são necessárias. Para instalá-las, basta executar o comando a seguir.
```console
username@user-computer:~$ sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

Antes de utilizar as ferramentas, é necessário iniciar um *software* chamado *rosdep*. É necessário executar os comandos a seguir.
```console
username@user-computer:~$ sudo apt install python3-rosdep
```
```console
username@user-computer:~$ sudo rosdep init
```
```console
username@user-computer:~$ rosdep update
```
Pronto! **ROS** está configurado e pronto para usar.

## 9. Plugin de inteface ROS para CoppeliaSim
Para configurar o plugin de interface **ROS** para o **CoppeliaSim**, é necessário primeiro criar um *workspace*. Em uma pasta adequada, execute os comandos abaixo. **OBS:** o nome *"IEEEOpenEquipeAtena"* pode ser alterado para qualquer outro - o nome do *workspace* não é tão relevante.
```console
mkdir IEEEOpenEquipeAtena
```
```console
cd IEEEOpenEquipeAtena
```
```console
mkdir src
```
```console
catkin_make
```
Um primeiro processo de configuração do *workspace* será realizado. Depois disso, será necessário clonar o [repositório do plugin](https://github.com/CoppeliaRobotics/simExtROS) (que é o plugin propriamente dito) através dos comandos a seguir.
```console
cd src
```
```console
git clone --recursive https://github.com/CoppeliaRobotics/simExtROS.git sim_ros_interface
```

Caso o comando *git* não seja reconhecido, é necessário instalar este *software* utilizando o comando abaixo.

```console
username@user-computer:~$ sudo apt-get install git 
```
Depois disso, volte à pasta do *workspace* utilizando o comando abaixo.
```console
cd ..
```
Por fim, execute o comando abaixo para compilar o plugin.
```console
catkin_make
```
Após a finalização do processo, será necessário copiar o arquivo *libsimExtROS.so* para a pasta extraída do **CoppeliaSim**. Para isso, acesse a pasta utilizando o comando a seguir.

```console
cd devel/lib/
```
Encontre o arquivo em questão e faça a cópia utilizando o comando a seguir, onde *$COPPELIASIM_ROOT_DIR* deve ser substituído pelo caminho no qual os arquivos do **CoppeliaSim** estão localizados (a pasta extraída).

```console
cp libsimExtROS.so $COPPELIASIM_ROOT_DIR
```

Caso seja perguntado, substitua o arquivo existente na pasta do **CoppeliaSim**. 

O último passo será definir a variável de ambiente *$COPPELIASIM_ROOT_DIR* toda vez que o terminal é aberto. Para isso, utilize os comandos abaixo, substituindo *INSIRA_CAMINHO_PARA_O_COPPELIA_AQUI* pelo caminho para a pasta extraída do **CoppeliaSim**. 

**OBS:** para obter o caminho , acesse a pasta em questão e utilize o comando *pwd*.

 ```console
username@user-computer:~$ echo "export COPPELIASIM_ROOT_DIR=INSIRA_CAMINHO_PARA_O_COPPELIA_AQUI" >> ~/.bashrc
```

```console
username@user-computer:~$ source ~/.bashrc
```
## 10. OpenCV
*Verificar se o ROS já vem com OpenCV.* 

## 11. Tesseract e 12. Leptonica
As ferramentas **Tesseract** e **Leptonica** são utilizadas na detecção dos números arábicos. Para instalá-lo, basta executar os comandos a seguir.

```console
username@user-computer:~$ sudo add-apt-repository ppa:alex-p/tesseract-ocr
```
```console
username@user-computer:~$ sudo apt-get update
```
```console
username@user-computer:~$ sudo apt install tesseract-ocr
```
```console
username@user-computer:~$ sudo apt install libtesseract-dev
```
Além disso, execute os comandos a seguir. Se já estiverem instalados, o comando não fará nenhuma alteração no sistema.

```console
username@user-computer:~$ sudo apt-get install g++ # or clang++ (presumably)
```

```console
username@user-computer:~$ sudo apt-get install autoconf automake libtool
```

```console
username@user-computer:~$ sudo apt-get install pkg-config
```

```console
username@user-computer:~$ sudo apt-get install libpng-dev
```

```console
username@user-computer:~$ sudo apt-get install libjpeg8-dev
```

```console
username@user-computer:~$ sudo apt-get install libtiff5-dev
```

```console
username@user-computer:~$ sudo apt-get install zlib1g-dev
```
