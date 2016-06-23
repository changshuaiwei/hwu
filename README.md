# hwu

AUTHOR: Changshuai Wei

CONTACT: weichangshuai@gmail.com	

YEAR: 2016

LICENSE: Released under GNU General Public License, v2 (see
COPYING.txt)

DOCUMENTATION: http://changshuaiwei.github.io/


COMPILATION: You will need a standard C++ compiler such as GNU g++  (version 3), as well as Boost c++ library (v1.55.0) and Eigen c++ library(v3.2).


Using HWU:

1:a simple one

hwu --bfile NIC --hwu --wIBS-wt --out NIC.rst

2:a complicated one

hwu --bfile NIC --hwu --dv 3 --cov all.cov.txt --flt --mp 20 --force-core  --cov-wt cov1.txt --out NIC.rst

##Options

--bfile <string> : read plink binary format data files

--file <string>: read text format data files

--hwu: perform HWU analysis

--out <string>: output files

--wIBS-wt: use weighted IBS to construct latent population structure

--IBS-wt: use IBS to construct latent population structure

--cov-wt <string> : use covariates in <string> files to construct latent population structure

--dv <int>: output the most significant <int> SNPs (for high demensional scan)

--write-Wmt <string> : output kappa matrix for latent population structure to <string> file

--flt : use float accuracy when calculate the rank of SNPs (for high demensional scan)

--read-Wmt <string>: read kappa matrix stored in <string> file

--cov <string>: read covariates that used for covariates adjustment in <string> file

--PCwt <int>: calculate the first <int> eigen vectors for matrix kappa

