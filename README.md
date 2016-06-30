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

##Options

--bfile `string` : read plink binary format data files

--file `string`: read text format data files

--hwu: perform HWU analysis

--out `string`: output files

--wIBS-wt: use weighted IBS to construct latent population structure

--IBS-wt: use IBS to construct latent population structure

--cov-wt `string` : use covariates in `string` files to construct latent population structure

--dv `int`: output the most significant `int` SNPs (for high demensional scan)

--write-Wmt `string` : output kappa matrix for latent population structure to `string` file

--flt : use float accuracy when calculate the rank of SNPs (for high demensional scan)

--read-Wmt `string`: read kappa matrix stored in `string` file

--cov `string`: read covariates that used for covariates adjustment in `string` file

--PCwt `int`: calculate the first `int` eigen vectors for matrix kappa

##compilation

###For visual studio

Make sure you compile with optimization enabled. This can easily gain you a factor of ten or more.

Configuring your project for optimal performance

    Open the project properties page (Project | Properties), in the C/C++ folder open the Code Generation page. Under Enable Enhanced Instruction Set, switch to Streaming SIMD Extensions 2 (/arch:SSE2)
    Open the project properties page (Project | Properties), in the C/C++ folder open the Language page. Under Open MP Support, switch to Yes (/openmp).
    In case you are on a 64 bit machine, open the configuration manager (Project | Properties | Configuration Manager...). From here, select <New...> under Active solution platform:. Next, choose x64 and confirm the dialog with OK. Once you are back in the main window, switch from Win32 to x64 in order to create 64 bit builds of your program. 

Since boost::thread is used here, we might not use openMP for Eigen

need to build boost lib

    run bootstrap.bat
    run b2
    go to properties->linker->general->additional library, add "$Root$\boost\boost_1_55_0\stage\lib"
