# hwu

AUTHOR: Changshuai Wei

CONTACT: weichangshuai@gmail.com	

YEAR: 2016

LICENSE: Released under GNU General Public License, v2 (see
COPYING.txt)

Precompiled excutable for windows and unix, as well as example data files can be found at http://changshuaiwei.github.io/software.html#HWU

COMPILATION: You will need a standard C++ compiler such as GNU g++  (version 3), as well as Boost c++ library (v1.55.0) and Eigen c++ library(v3.2).


Using HWU:

1:a simple one

hwu --bfile NIC --hwu --wIBS-wt --out NIC.rst

2:a complicated one

hwu --bfile NIC --hwu --dv 3 --cov all.cov.txt --flt --mp 20 --force-core  --cov-wt cov1.txt --out NIC.rst

3:another complicated one

hwu --bfile NIC --hwu --screen 2 --wIBS-wt --mp 7  --PCwt 20 --out NIC.rst

##Options

--bfile `string` : read plink binary format data files

--file `string`: read text format data files

--hwu: perform HWU analysis

--out `string`: output files

--mp `int`: parallelize computations to `int` numbers of cpu cores

--wIBS-wt: use weighted IBS to construct latent population structure

--IBS-wt: use IBS to construct latent population structure

--cov-wt `string` : use covariates in `string` files to construct latent population structure

--dv `int`: output the most significant `int` SNPs (for high demensional scan)

--write-Wmt `string` : output kappa matrix for latent population structure to `string` file

--flt : use float accuracy when calculate the rank of SNPs (for high demensional scan)

--read-Wmt `string`: read kappa matrix stored in `string` file

--cov `string`: read covariates that used for covariates adjustment in `string` file

--PCwt `int`: calculate the first `int` eigen vectors for matrix kappa

--screen `int`: screen SNPs using standardized HWU, and calculate p-value of highest ranked `int` SNPs (for ultra-high demensional scan)

##compilation&build

First download [Eigen](https://eigen.tuxfamily.org/index.php?title=Main_Page) and [Boost](https://www.boost.org/doc/libs/1_55_0/) under code/dependency. Unzip both, and then install boost by following steps [here](https://www.boost.org/doc/libs/1_55_0/more/getting_started/unix-variants.html#easy-build-and-install).

###For g++

For release:
    g++ -static -L dependency/boost_1_55_0/stage/lib -I dependency/eigen-3.4.0 -I dependency/boost_1_55_0 -pthread -msse2 *.cpp -lboost_system -lboost_thread -lrt -w -O3 -o build/hwu

For debug:
    g++ -static -L dependency/boost_1_55_0/stage/lib -I dependency/eigen-3.4.0 -I dependency/boost_1_55_0 -pthread -msse2 -g *.cpp -lboost_system -lboost_thread -lrt -w -O3 -o build/hwu_debug

###For VS code

Follow steps [here](https://code.visualstudio.com/docs/cpp/introvideos-cpp). And refer to above g++ for args needed in corresponding json config.


###For visual studio (2015 version, outdated)

Make sure you compile with optimization enabled. This can easily gain you a factor of ten or more.

Configuring your project for optimal performance

    Open the project properties page (Project | Properties), in the C/C++ folder open the Code Generation page. Under Enable Enhanced Instruction Set, switch to Streaming SIMD Extensions 2 (/arch:SSE2)
    Open the project properties page (Project | Properties), in the C/C++ folder open the Language page. Under Open MP Support, switch to Yes (/openmp).
    In case you are on a 64 bit machine, open the configuration manager (Project | Properties | Configuration Manager...). From here, select <New...> under Active solution platform:. Next, choose x64 and confirm the dialog with OK. Once you are back in the main window, switch from Win32 to x64 in order to create 64 bit builds of your program. 

Since boost::thread is used here, we might not use openMP for Eigen

need to build boost lib

    use the VS comand prompt
    run bootstrap.bat
    run b2
    go to properties->linker->general->additional library, add "$Root$\boost\boost_1_55_0\stage\lib"


