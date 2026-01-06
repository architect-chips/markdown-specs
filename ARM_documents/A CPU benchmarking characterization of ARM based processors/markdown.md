

УДК: 004.27

# A CPU benchmarking characterization of ARM based processors

R. G. Reed<sup>a</sup>, M. A. Cox, T. Wrigley, B. Mellado

School of Physics, University of the Witwatersrand, 1 Jan Smuts Avenue, Braamfontein, Johannesburg, 2000, South Africa

E-mail: <sup>a</sup>robert.reed@cern.ch

Received September 30, 2014

Big science projects are producing data at ever increases rates. Typical techniques involve storing the data to disk, after minor filtering, and then processing it in large computer farms. Data production has reached a point where on-line processing is required in order to filter the data down to manageable sizes. A potential solution involves using low-cost, low-power ARM processors in large arrays to provide massive parallelisation for data stream computing (DSC). The main advantage in using System on Chips (SoCs) is inherent in its design philosophy. SoCs are primarily used in mobile devices and hence consume less power while maintaining relatively good performance. A benchmarking characterisation of three different models of ARM processors will be presented.

Keywords: High data throughput, Computing, Big Data, ARM System on Chips, Benchmarking

## Характеристика тестирования центрального процессора на базе процессоров ARM

Р. Г. Рид, М. Кокс, Т. Ригли, Б. Мелладо

Отделение Физики, Университет Витватерсранда, Южная Африка, 2000, Йоханнесбург, 1 Ян Смут  
Авенно

Большие научные проекты генерируют данные на всё более возрастающих скоростях. Типичные методы включают в себя хранение данных на диске, после незначительного фильтрования, а затем их обработку на больших компьютерных фермах. Производство данных достигло той точки, когда требуется обработка в режиме on-line, чтобы отфильтровать данные до управляемых размеров. Потенциальное решение включает в себя использование низко затратных процессоров ARM с маленькой мощностью в больших массивах для обеспечения массивного распараллеливания для вычислений потока данных (DSC). Главное преимущество в использовании систем на одном кристалле (SoCs) присуще самой философии этой разработки. Системы на микросхеме, прежде всего, используются в мобильных устройствах и, следовательно, потребляют меньше энергии при своей относительно хорошей производительности. Дано описание тестирования трех различных моделей процессоров ARM.

Ключевые слова: высокая вычислительная пропускная способность, большие данные, система на ARM чипе, эталонные тесты

Citation: *Computer Research and Modeling*, 2015, vol. 7, no. 3, pp. 581–586.

## 1. Introduction

The term "Big Data" has caught on in the mainstream media and science worlds. While this word in now ubiquitous and almost exhausted in it's use it still identifies an important issue in the science community. Processing data is getting more difficult due to the shear amount being produced. In the year 2022 the ATLAS detector will be upgraded and in doing so will produce in the order of Petabytes per second of raw data [ATLAS C 2012 Letter of Intent... 2012]. There is no feasible way to process this much data in a reasonable amount of time. This is largely due to external Input/Output (I/O) bottlenecks present in current super computing systems. A team at the University of the Witwatersrand, Johannesburg is actively involved in the development of a computing system which is both cost-effective and able to provide high data throughputs in the order of Gigabits per second. There are four widely accepted computing paradigms. The first, and most commonly known, is the High Performance Computing paradigm (HPC) which is focused on the raw number of calculations performed per second. The second is the Many Task Computing (MTC) which focusses on the number of jobs that can be completed in a given amount of time. Real Time Computing (RTC) involves very strict restrictions on execution times (such as air-bag sensors or process controls). Finally, a fourth paradigm called Data Stream Computing (DSC) involves the processing of large amounts of data with no off-line storage. The processing unit that the team at the University of the Witwatersrand is designing falls under this DSC paradigm and provides the motivation for this paper. In order to design a processing unit that is capable of handling high throughputs the system must be very well balanced. A better understanding of the SoCs is needed in order to achieve this. Presented below is a CPU benchmarking characterisation of three ARM based SoCs.

## 2. Hardware

Three ARM system on chips will be characterised. The Cortex-A7, Cortex-A9 and Cortex-A15 are available on the Cubieboard2, Wandboard and Odroid-XU+E platforms [Cubieboard 2013 Fedora 19..., 2013; Freescale..., 2009; Hardkernel..., 2013]. The specifications of each board can be found in Tab. 1.

Table 1: Specifications of the ARM platforms.

|                      | Cortex-A7           | Cortex-A9           | Cortex-A15          |
|----------------------|---------------------|---------------------|---------------------|
| Platform             | Cubieboard A20      | Wandboard Quad      | ODROID-XU+E         |
| SoC                  | Allwinner A20       | Freescale i.MX6Q    | Samsung S410        |
| Cores                | 2                   | 4                   | 4 (+ 4 Cortex-A7)   |
| Max. CPU Clock (MHz) | 1008                | 996                 | 1600                |
| L2 Cache (kB)        | 256                 | 1024                | 2048                |
| Floating Point Unit  | VFPv4 + NEONv2      | VFPv3 + NEON        | VFPv4 + NEONv2      |
| RAM (MB)             | 1024                | 2048                | 2048                |
| RAM Type             | 432 MHz 32 bit DDR3 | 528 MHz 64 bit DDR3 | 800 MHz 64 bit DDR3 |
| Ethernet (Mb/s)      | 100                 | 400                 | 100                 |
| PCI-Express (Gb/s)   | -                   | 5                   | -                   |
| 2014 Retail (USD)    | 65                  | 129                 | 169                 |

## 3. CoreMark

CoreMark was developed by The Embedded Microprocessor Benchmark Consortium (EEMBC) and has been proposed as the replacement for Dystone by ARM Holdings [Dunn and Marini, 2009]. The benchmark is specifically designed for Embedded Microprocessors which makes it an ideal benchmark to use. There are numerous pros to using CoreMark and they are summarised by Eric Schorn, VP marketing, Processor Division, ARM "We believe that CoreMark represents a significant

improvement on the current Dhrystone benchmarks by measuring processor behaviour that could more realistically be expected in a real application. Combined with greater access to the results, this new benchmark should enable developers to obtain an unambiguous representation of processor performance enabling comparisons between competing processors to be made.” [Dunn and Marini, 2009].

![Figure 1: Two plots showing performance characteristics of Cortex-A7, Cortex-A9, and Cortex-A15 processors. Plot (a) shows Percentage Improvements from Worst Combination [%] versus Different Flag Combinations (0 to 15). Plot (b) shows Coremark Result [Iterations/s] versus Iteration counts (log scale, 1 to 131072).](e863446d7d263c68be9402afd63668ac_img.jpg)

Figure 1: Two plots showing performance characteristics of Cortex-A7, Cortex-A9, and Cortex-A15 processors. Plot (a) shows Percentage Improvements from Worst Combination [%] versus Different Flag Combinations (0 to 15). Plot (b) shows Coremark Result [Iterations/s] versus Iteration counts (log scale, 1 to 131072).

Fig. 1: a) Different flag combinations for compiling and b) Coremarks as a function of Iteration counts

CoreMark uses four common algorithms found in realistic applications such as matrix manipulation, linked list manipulation, state machine operations and cyclic redundancy checks. This provides an overall “realistic” performance of the chips. Additionally, CoreMark has strict online result submission guidelines. This provides a trustworthy and strong database of results with which to compare your own chips. The result is reported as the number of iterations of these four common algorithms per second. Figure 1a) shows the performance of different combinations of compiler flags. The best performing flag combinations can be seen in Tab. 2

Table 2: Best Performing Flag Combinations

| Architecture | Flag Combination                                                                 |
|--------------|----------------------------------------------------------------------------------|
| Cortex-A7    | -mfloat-abi=hard -ffastmath -O3 -mfpu=neon-vfpv4 -march=armv7-a -mtune=cortex-a7 |
| Cortex-A9    | -mfloat-abi=hard -ffastmath -O3 -mfpu=neon -march=armv7-a                        |
| Cortex-A15   | -mfloat-abi=hard -ffastmath -O3 -mfpu=neon-vfpv4 -march=armv7-a                  |

Figure 1b) shows the performance rise to a plateau for increasing iteration count. A particular criteria for result submission is to run the test for at least 10 seconds. This will be at approximately 2048 iterations and is well onto the plateau which illustrates why the database results are a fair comparison.

Figure 2 shows CoreMark results for various different systems. The first three bars represent the Cortex-A7, A9, and A15 results that we measured ourselves and the last four are from the CoreMark online database [EEMBC OnlineDatabase...]. The chosen systems are: a low powered Intel Atom 330, Intel Atom N2800, mid range Intel i7 2600 and a high end Intel i7 3930k. From Figure 2a) it can been seen that the high end Intel i7's are much more powerful per core. The Cortex-A9 is similar to the Atom 330 and like wise the Cortex-A15 is similar to the Atom N2800. Both sets of chips were manufactured around the same time. It must be noted that the Atom N2800 only has two cores while the Cortex-A15 has four, which means that the overall performance of the Cortex-A15 will still be better. Looking at the performance per watt in Fig 2b) the complete opposite is observed with the Cortex-A15 being over 3 times more efficient than the Intel i7 3930k. The power consumption measured for the Cortex chips included all peripherals while the Thermal Design Power is quoted for the Intel chips. This means the power consumption of the Intel chips would most likely increase when taking into account all peripherals.

![Figure 2: Two bar charts comparing Measured and Database CoreMark results for various ARM systems (Cortex-A7, Cortex-A9, Cortex-A15, Atom 330, Atom N2800, Intel i7-2600, Intel i7-3930k). Chart (a) shows CoreMark Normalised to Cores, where the Database results are significantly higher than Measured results for all systems. Chart (b) shows CoreMark Normalised to Power Consumption (CoreMark/Watt), where the Database results are generally higher than Measured results, except for the Intel i7-3930k.](7fb5215fd72210a2e4cce6df55550c89_img.jpg)

Figure 2: Two bar charts comparing Measured and Database CoreMark results for various ARM systems (Cortex-A7, Cortex-A9, Cortex-A15, Atom 330, Atom N2800, Intel i7-2600, Intel i7-3930k). Chart (a) shows CoreMark Normalised to Cores, where the Database results are significantly higher than Measured results for all systems. Chart (b) shows CoreMark Normalised to Power Consumption (CoreMark/Watt), where the Database results are generally higher than Measured results, except for the Intel i7-3930k.

Fig. 2: a) CoreMark results for various systems normalised to the number of cores and b) CoreMark per Watt for various systems

## 4. High Performance Linpack

Coremark gives an overall performance of a system but to understand the computing capability one must use a benchmark like High Performance Linpack. This benchmark uses matrix manipulations to give the number of Floating Point Operations Per Second (FLOPS) that a system can achieve in double precision [Dongarra et al, 2003]. It was introduced by Jack Dongarra in 1979 and first reported in the LINPACK Users Guide [Dongarra et al, 1979]. HPL is currently being used on the TOP500 Super-Computing List [TOP500, 2013] which makes the benchmark a necessity when characterising the ARM CPUs since it is largely accepted and understood. HPL is scalable and specifically targeted at distributed memory clusters. An important measurement is the number of FLOPS measured per Watt of the system. This can be used to compare to the GREEN500 [GREEN500, 2013] which is a supercomputing list based on efficiency rather than pure performance with results measured in GFLOPS/Watt.

![Figure 3: Two charts showing HPL Double Precision results for Cortex-A7, Cortex-A9, and Cortex-A15. Chart (a) shows HPL Score [GFlops] versus Memory Used [MB]. The Cortex-A15 achieves the highest score (around 7.5 GFlops) and uses the most memory (up to 1,500 MB). The Cortex-A9 achieves a lower score (around 2.5 GFlops) and uses less memory. The Cortex-A7 achieves the lowest score (around 1 GFlops) and uses the least memory. Chart (b) shows HPL Normalised to Power (GFLOPS/Watt) for the same systems. The Cortex-A15 achieves the highest normalized performance (around 0.8 GFLOPS/Watt), followed by Cortex-A9 (around 0.45 GFLOPS/Watt), and Cortex-A7 (around 0.25 GFLOPS/Watt).](954ff3c220707f98bcb2c4b197bd7d9f_img.jpg)

Figure 3: Two charts showing HPL Double Precision results for Cortex-A7, Cortex-A9, and Cortex-A15. Chart (a) shows HPL Score [GFlops] versus Memory Used [MB]. The Cortex-A15 achieves the highest score (around 7.5 GFlops) and uses the most memory (up to 1,500 MB). The Cortex-A9 achieves a lower score (around 2.5 GFlops) and uses less memory. The Cortex-A7 achieves the lowest score (around 1 GFlops) and uses the least memory. Chart (b) shows HPL Normalised to Power (GFLOPS/Watt) for the same systems. The Cortex-A15 achieves the highest normalized performance (around 0.8 GFLOPS/Watt), followed by Cortex-A9 (around 0.45 GFLOPS/Watt), and Cortex-A7 (around 0.25 GFLOPS/Watt).

Fig. 3: Double precision High Performance Linpack results for Cortex-A7, Cortex-A9 and Cortex-A15

Figure 3a) shows the typical results reported by HPL for double precision floating point numbers. For clarity the array size (x-axis) is shown as the amount of memory used rather than the actual NxN matrix size. The Cortex-A15 performs the best with a GFLOP score over 3 times higher than the Cortex-A9. The Cortex-A7 is designed to be low performance with low power consumption so it's not surprising that it achieves approximately 0.8 GFLOPS. For very small array sizes (small sizes in RAM) there are large overheads when HPL is running. This is expected to be due to the calculation on given small arrays being shorter than the time taken to populate and fetch data from RAM.

Figure 3b) shows the double precision HPL Efficiency expressed as GFLOPS/Watt. The best performing result is taken. The Cortex-A15 is not 3 times the efficiency of the Cortex-A9. It is only a factor of 1.8. The Cortex-A15 attains a peak of 0.87 GFLOPS/Watt. This would be placed at 110th spot in the Green500 list [Green500-Top200, 2013]. It's interesting to see that the performance efficiency doubles from one architecture to the next. It is surprising to see that the Cortex-A7 has such low efficiency but this is attributed to all the external peripherals that increase the power consumption.

## 5. FFTW

The Fastest Fourier Transform in the West (FFTW) is a benchmark based on the discrete Fourier transform [Rajovic et al, 2013]. This type of transform is unique in that it has a finite number of elements and thus can be solved computationally. The transform allows a change of domain for a given set of data. The FFTW reports data in MFLOPS =  $(5\log_{10}N)/t$ , where N is the size of the FFT and t is the time taken to compute the FFT. This is a theoretical performance but found to be quite accurate as it can be compared to results obtained for HPL. A second result reported is the throughput. Using the size of the FFT and the time taken to compute the MB/s throughput can be calculated. This is useful in the context of Data Stream Computing.

![Figure 4 shows two plots related to FFTW benchmarks for ARM Cortex-A7, A9, and A15. Plot (a), 'Theoretical FFTW Performance', shows Performance (GFLOPS) versus FFT Length [N]. The Cortex-A15 (green line) achieves the highest performance, peaking around 6.5 GFLOPS at N=2^16. The Cortex-A9 (red line) peaks around 2.5 GFLOPS at N=2^16. The Cortex-A7 (blue line) peaks around 1.5 GFLOPS at N=2^16. Plot (b), 'Theoretical FFTW Throughput', shows Throughput (MB/s) versus FFT Length [N]. The Cortex-A15 (green line) achieves the highest throughput, peaking around 1,200 MB/s at N=2^16. The Cortex-A9 (red line) peaks around 800 MB/s at N=2^16. The Cortex-A7 (blue line) peaks around 300 MB/s at N=2^16.](6f1efa91fb9b476380af7a35db4f14bf_img.jpg)

Figure 4 shows two plots related to FFTW benchmarks for ARM Cortex-A7, A9, and A15. Plot (a), 'Theoretical FFTW Performance', shows Performance (GFLOPS) versus FFT Length [N]. The Cortex-A15 (green line) achieves the highest performance, peaking around 6.5 GFLOPS at N=2^16. The Cortex-A9 (red line) peaks around 2.5 GFLOPS at N=2^16. The Cortex-A7 (blue line) peaks around 1.5 GFLOPS at N=2^16. Plot (b), 'Theoretical FFTW Throughput', shows Throughput (MB/s) versus FFT Length [N]. The Cortex-A15 (green line) achieves the highest throughput, peaking around 1,200 MB/s at N=2^16. The Cortex-A9 (red line) peaks around 800 MB/s at N=2^16. The Cortex-A7 (blue line) peaks around 300 MB/s at N=2^16.

Fig. 4: FFTW benchmarks for the ARM Cortex-A7, A9 and A15 showing best-case multi-core and multi-process performance (a) and theoretical FFT throughput (b)

Figure 4a) shows the performance for various FFT sizes, N. It can be seen that the peak performances are similar to that of HPL in Fig. 3a). The shape is not smooth and this is due to the CPU specific components such as cache sizes, memory controllers and architectures. Figure 4b) shows the theoretical throughput that could be achieved if there were no bottle necks. Unfortunately the I/O performance is drastically limiting. Table 1 shows the connectivity of each SoC. The Cortex-A15 and Cortex-A7 both are limited to 1 Gb Ethernet while the Cortex-A9 has a PCIe lane at 5 Gb. For larger N values around  $2^{16}$  we see the SoCs reaching the 1 Gb throughput range. The Cortex-A15 has a secondary peak at this point in the order of 5 Gb. This indicates that a Cortex-A15 could saturate a single PCIe lane for complex FFT problems.

## 6. Conclusion

The performance of the Atom is comparable to the Cortex A9 but looking at the power consumption it can be seen that the Atoms are less power efficient. The power consumption of the Atoms is based on their chip specifications alone so taking into account the need for a motherboard and all peripherals this is expected to increase. The Cortex-A7 does not have sufficient performance as seen in the HPL results in Fig 3a. There are newer ARM cores available such as the Cortex-A50 series [Holdings A Cortex-A50...] and new Atoms such as the Z34XX Series [Intel..., 2014] which will usher in the 64 bit architectures. The new Atoms are SoCs and the power consumption will be better than the Atoms shown in this paper. These new ARM architectures will have double precision NEON extensions which will drastically increase their performance as current NEON extensions are only single precision. Intel have opened their fabrication plants to the new Cortex-A53 on their 12 nm trigate technology [Martenson, Altera, 2013] so the expected performance of these ARM CPUs and possibly the newer Atoms will increase significantly and could offer a cheaper alternative for parallel computing. The same can be said for the new generation of Atoms.

## References

ATLAS C 2012 Letter of Intent for the Phase-II Upgrade of the ATLAS Experiment URL: <http://cds.cern.ch/record/1502664?ln=en>

Cubieboard 2013 Fedora 19 For Cubieboard(A20) is Available URL: <http://cubieboard.org/2013/07/19/fedora-19-for-cubieboarda20-is-available/>

Dongarra J. J., Luszczek P. and Petitet A. Concurrency and Computation: Practice and Experience 15. 2003. 803-820 ISSN 1532-0626 URL: <http://doi.wiley.com/10.1002/cpe.728>

Dongarra J., Bunch J., Moler C. and Stewart G. LINPACK: users' guide (SIAM). 1979. URL: <http://books.google.ch/books?id=AmSm1n3Vw0cC&lpg=PR5&ots=EDFdqJhr8x&dq=infoV/o3AhttpV/o3AV/02F%02Fs3da3171290b34600.scholar.google.comV/o2F0&lr&pg=SL2-PA1#v=onepage&q&f=false>

Dunn L. and Marini C. ARM Announces Support For EEMBC CoreMark Benchmark — ARM. 2009. URL: <http://www.arm.com/about/newsroom/25152.php>

EEMBC OnlineDatabase — The Embedded Microprocessor Benchmark Consortium URL: <http://www.eembc.org/coremark/>

Freescale 2009 i. MX 6 Series of Applications Processors Tech. rep. URL: [http://www.freescale.com/webapp/sp/site/taxonomy.jsp?code=IMX6X\\_SERIES](http://www.freescale.com/webapp/sp/site/taxonomy.jsp?code=IMX6X_SERIES)

GREEN500. The Green500 List. 2013. URL: <http://www.green500.org/>

Green500-Top200 The Green500 List — November 2013 — The Green500 URL <http://www.green500.org/lists/green201311&green500from=101&green500to=200>

Hardkernel 2013 ODDROID XU+E URL: [http://hardkernel.com/main/products/prdt\\_info.php?g\\_code=G137463363079&tab\\_idx=2](http://hardkernel.com/main/products/prdt_info.php?g_code=G137463363079&tab_idx=2)

Holdings A Cortex-A50 Series - ARM URL: <http://www.arm.com/products/processors/cortex-a50/>

Intel 2014 Intel Atom Processor Z34XX Series for Smartphones and Tablets URL: <http://www.intel.com/content/www/us/en/processors/atom/atom-z34xx-smartphones-tablets-brief.html>

Martenson Sue, Altera A. Newsroom — Altera Announces Quad-Core 64-bit ARM Cortex-A53 for Stratix 10 SoCs. 2013. URL: <http://newsroom.altera.com/press-releases/nr-altera-arm-a53.htm>

Rajovic N., Carpenter P. M., Gelado I., Puzovic N., Ramirez A. and Valero M. Proceedings of the International Conference for High Performance Computing, Networking, Storage and Analysis on — SC '13. New York, USA. 2013. P. 1–12. ISBN 9781450323789

TOP 500. November 2013 — TOP500 Supercomputer Sites. 2013. URL: <http://www.top500.org>