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
