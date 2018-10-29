# Array-Toolbox  
Distributed Audio Array Matlab Toolbox for public viewing and use. For more information, read here: <http://vis.uky.edu/distributed-audio-lab/>  
  
*Organized by **Yushuai Zhang***  
  
# Delay函数部分  
* delayint – This is the simplest and fastest delay function. It applies a delay or set of delays to the input signal matrix by substituting the signal samples in the output array with an offset corresponding to the delay. Sub-sample delays ARE NOT possible with this program. Delays are always integer multiples of the sampling interval.  
  
* delaytab – This delay function breaks the delay into an integer multiple and fractional component of the sampling period. The integer part of the delay is handled as it is in delayint. The fractional difference is rounded off to the nearest sub-sample interval described by an input table of FIR interpolation coefficients. An FIR table for this program can be generated with several options using the program subsamplefir.  
  
* delayt – This delay function breaks the delay into an integer multiple and fractional component of the sampling period. The integer part of the delay is handled as it is in delayint. The fractional part is used to create an FIR sub-sample delay filter with a 4-coefficients cosine square-weighted sinc function (NOTE: the filter order and type of filter can be changed by editing the appropriate comment lines in the mfile), and the sub-sample delay is realized through filtering the integer delayed vector by this filter. This function is more flexible than delaytab; however, it requires more computation since the filter coefficients have to be computed for each arbitrary delay.  
  
* delayf – This delay function implements the delay in the frequency domain by multiplying the zero-padded FFT of the input vector by e^{-j*\omega*delay}. This has the potential to be the most accurate delay implementation, especially for a true band-limited signal; however, it requires more computations than any other delay function.  
  
* subsamplefir – This function creates tables of FIR filter coefficients for filters that implement sub-sample delays at equal sub-increments over the original sample period. The filter order and type are determined through the input arguments. The resulting matrix of coefficients can be directly used in the delaytab function to implement sub-sample delays.  
  
## 测试用例  
  
The following scripts are used to test and demonstrate the delay functions described above:  
  
*testdelayreal – This script generates a real signal and steps through a sequence of sub-sample delays using the methods in delayf, delayt, delaytab, and delayint . Examples of each window are shown graphically as the signal shifts relative to the original. An analysis is also done to compare the time required for each algorithm and difference/error of delayed signal with the frequency domain delayed version.  
  
*testdelaycomplex – This script generates a complex signal using the Hilbert transform and steps through a sequence of sub-sample delays on the complex signal using the methods in delayf, delayt, delaytab, and delayint . Examples of each window are shown graphically as the envelope of the signal shifts relative to the original. An analysis is also done to compare the time required for each algorithm and difference/error of delayed signal with the frequency domain delayed version.  
  
# 延迟估计器  
* delayesttm – This function estimates the relative delay between signals using the cross-correlation function. The input signal segments must be the same length and sampled with respect to the same time reference. Various signal processing options are built into this function through an optional data structure input, including detrending, center clipping, and interpolating to estimate delays on a finer grid resolution than the sampling rate. See comparedelay for example of use.  
  
* delayestfr – This function estimates the relative delay between signals using the group delay of the cross-correlation function. The group delay is estimated as a weighted average of the unwrapped phase gradients, where the weights are the magnitudes of the cross-correlation spectrum. The signal segments must be the same length and sampled with respect to the same time reference. Various signal processing options are built into this function through an optional data structure input, including detrending, and limiting the frequency range over which the group delay is estimated. See comparedelay for example of use.  
  
## 测试用例  
  
* comparedelay – This script runs a Monte Carlo simulation for delay estimations between two band-limited pulse signals in noise using the functions delayesttm and delayestfr. Performances for each run are presented in the titles of two figures showing the test signals (processing loop is paused after each run so the figures can be observed).  
# 麦克风阵列放置和分析模块  
* regmicsline（线阵） – This functions generates coordinates for a line array of equally spaced microphones.  
  
* resmicsplane（平面阵，包括六麦克风） – This function generates coordinates for a plane array of either rectilinearly or hexagonally spaced microphones.  
  
* regmicsperim – This function generates coordinates for a plane array of microphones around the perimeter of an area.  
  
* mposanaly – This function finds all possible subsets of microphones in an array taken K at a time. It outputs these subsets to a matrix along with their spacing statistics, such as the mean, minimum, maximum, and standard deviation. Since this function uses an N choose K operation to enumerate all possible subsets, care should be taken to ensure that an unwieldy amount of combinations are not generated.  
  
## Example/Test Scripts  
  
* testmicgeom – This script generates a regular line array, a regular plane array, a hexagonal plane array, and a random plane array with analyses using the above functions. Examples of microphone placements are shown graphically. For a random array placement, mposanaly is used to find all possible microphone pairs and rank them according to distance.  
  
* testmicperim – This script generates a regular perimeter array using regmicsperim. Examples of microphone placements are shown graphically.  
  
#模拟功能  
* simarraysig – 模拟麦克风阵列输入的信号，需要提供麦克风阵列位置和源位置。Optional inputs allow for the placement of scatterers to generate multi-path interference, and parameters to control the attenuation of sound in air. The attenuation parameter is in dB per Hz-meter, so the further the source is from the microphone and the higher the signal frequency, the greater the attenuation on the received signal. If using a recorded signal, it is suggested to trim the noise or non-signal part from the input signal (pad with zeros if it is necessary to extend the signal). Any additional signals before the actual source signal will be synchronized to the signal and not have the true noise effect. This function requires the function roomimpres to run, which requires atmAtten.  
  
* simarraysigim – 使用一种方法来描述在矩形房间中的声音。This function is similar to simarraysig above, except it simulates sound in a rectangular room using the image method described by J.B. Allen and D.A. Berkley in “Image Method for Efficiently Simulating Small-Room Acoustics,” J. Acoust. Soc. Am., Vol. 65, No. 4, Apr. 1979. In addition to the inputs described in simarraysig, a pair of opposite vertices of the rectangular room is required along with the reflectivity of each surface of the room. Optional parameters allow for setting the number of image scatterers based on a threshold for the scattering coefficients, and the degree of frequency dependent attenuation of the air path. This function requires the functions imagesim and roomimpres to run.  
  
* simimp – 产生类似于脉冲的信号，是巴特沃斯滤波器的脉冲响应。用于检查不同信号的频率如何影响阵列的功能。This generates an impulse-like signal that is effectively the impulse response of a Butterworth filter. The frequency range of the impulse can be specified. This can be used to examine how the frequency content of different signals impacts array functions like sound source location. The sounds can be played using soundsc in Matlab. For example, a narrowband signal sounds like a drip with tonal properties and the broadband high frequency sound like a click or a snap. If the band includes a broad range, then both high and low frequency sounds can be heard, a low bass-drum-like sound with a snap.  
  
* simtone – 这产生了一个音调脉冲信号，它是一个半正弦调制包络。 可以选择几种不同的包络。  
  
simnoise – 突发噪声信号。This generates a noise burst signal that is white noise modulated with an envelope. Several different envelopes can be selected.  
  
* imagesim – 基于矩形房间几何形状和表面的散射特性生成一系列散射参数（延迟和散射系数等）This generates a series of image scatterers (delays and scattering coefficients) based on a rectangular room geometry and scattering properties of the surfaces. The number of image scatterers is controlled by a threshold to stop generating scatterers once their scatterer coefficient drops below a certain value.  
  
* roomimpres – 输入与混响环境中声源和麦克风阵列相关联的参数，并为麦克风阵列创建脉冲响应。This inputs a sequence of scatterers (delays and scattering coefficients) associated with a sound source and receiver pair in a reverberant environment, the frequency attenuation coefficient, and creates an impulse response for the source receiver pair. This requires atmAtten to compute frequency-dependent attenuation based on humidity, temperature, and pressure.  
  
* atmAtten – 基于输入来计算传播声波的衰减。This function computes attenuation of the propagated sound wave based on inputs, which are temperature in degrees Celsius, static pressure in in. Hg, relative humidity in %, sound propagation distance, and frequency of sound (may be a vector). It does not account for spherical spreading. This program was written by Nathan Burnside 10/5/04, AerospaceComputing Inc., and is also published on Matlab Central.  
  
* SpeedOfSound – 在温度，湿度和气压的作用下返回测试环境中的声速This simple script returns the speed of sound in the test environment given the temperature, humidity, and air pressure; the inputs should be in units of Centigrade, percent, and mmHg, respectively.  
  
## 演示用例  
* test_multipath_sim – This script reads in audio file scare_crow.wav which is a single source recording of a male saying the words, “there was a scarecrow standing in the middle of the street.” It then creates a set of signals corresponding to this signal recorded over a linear array of microphones. Graphic and sound output compares the closest and furthest microphones with and without multipath scatterers. This script requires the wave file scare_crow.wav and functions SpeedOfSound, simarraysig, roomimpres, atmAtten, and regmicsline.  
  
* test_roomrev_sim – This script reads in audio file scare_crow.wav which is a single source recording of a male saying the words, “there was a scarecrow standing in the middle of the street.” It then creates a set of signals corresponding to this signal recorded over a linear array of microphones in a rectangular room with reverberations. Graphic and sound output compares the closest and furthest microphones. This script requires the wave file scare_crow.wav and functions SpeedOfSound, simarraysigim, roomimpres, atmAtten, imagesim, and regmicsline.  
  
#鸡尾酒会模拟  
* wav2sig – This function reads in wave files and stores all the sampled signals into a single matrix with an equal number of rows (samples) and same sampling rates, where each column represents the different wave files.  
  
* cocktailp – This function simulates placing sound sources at specified positions in a room and recording the resulting sound field with spatially distributed microphones. Its input is a matrix with columns being the sample sounds of interest. This matrix can be created by wav2sig from stored wave files. This function calls the general simulation functions simarraysigim, roomimpres, and imagesim.  
  
## 演示用例  
  
* runCocktailp – This test script shows an example of simulating a cocktail party recording from individually recorded signals. The microphone positions and the source positions for each individual recording can be set by the simulation. The script reads in 6 wave files, generates a planar distribution of microphones in a 3.6 by 3.6 by 2.2 meter room with mild room reverberation, plots the microphones and source positions, and plays 4 microphone recordings (randomly selected) of the simulated cocktail party. It calls the following functions from the ArrayToolbox: SpeedOfSound, atmAtten, wav2sig, cocktailp, simarraysig, simarraysigim, roomimpres, imagesim, and regmicsplane. It uses the following wave files: man1.wav, man2.wav, man3.wav, woman1.wav, woman2.wav, woman3.wav.  
  
# 信号处理函数  
* flattap – 创建一个锥形窗。This function creates a tapered window that is flat in the center and tapered on the ends with a Hann window. This is especially useful if processing with an FFT and correlating later, as in the case of the whitening or Phase Only Transform (PHAT) for sound source location. The tapers with a maximum point in the center tend to bias the correlation toward the center. This window overcomes that problem.  
  
* whiten – 将输入信号的FFT系数的模数缩放为1。输入和输出的相位相同，因此该操作有时被称为相位变换（PHAT）。This function scales the modulus of the FFT coefficients of input signals to 1, effectively whitening the signal. The phase is the same for input and output, and therefore this operation is sometimes referred to as the phase transform (PHAT). In addition to whitening the input, a special parameter can be selected to control the degree of whitening. For example a value of 1 will result in the PHAT, a value of 0 will leave the modulus unchanged. Any number between 0 and 1 will represent a transition between original modulus and the flat/white one and is referred to as partial whitening.  
  
* srpframenn – 此功能使用转向响应功率（SRP算法）从一组麦克风阵列信号创建声学图像。This function creates an acoustic image from a set of microphone array signals using a steered response power (SRP algorithm). It requires arweights and delayint to run. This particular version uses only integer shifts on the input signals for the delay and sum operation, and computes the coherent average power (rather than total average power), which does not include the power terms for each individual microphone signal. So the coherent power is effectively the cross-correlation between different microphone signals without the self-power terms, and can therefore be negative.  
  
* arweights –此功能根据麦克风阵列信号与视场（FOV）中感兴趣点的距离为麦克风阵列信号创建一组实际权重。对于此函数，权重与距离点的距离成反比并归一化，因此权重之和为1。This function creates a set of real weights for the microphone array signals based on their distance from the point of interest in the field of view (FOV). For this function the weights are inversely proportional to the distance from the point and normalized so the sum of weights are one.  
  
* cclip – 中心限幅，可用于消除低电平噪声This function performs various types of center clipping on audio data useful for removing low-level noise.  
  
##演示用例  
* testsprimage – This script creates an acoustic image using the function srpframenn. It simulates a simple impulse-like sound in an FOV of a perimeter array. It also uses the following functions: flattap, whiten, arweights, delayint, simarraysigim, regmicsperim, mposanaly, delayt, simimp, imagesim, and roomimpres. These must be in your current directory for this to run properly. The output is a plot of the SRP image with the simulated target position, microphone positions, and coherent noise source positions. The script randomly generates the target and noise source positions, so the simulation from this script is different every time. See script for modifying simulation parameters. An additional figure is generated to show the original microphone inputs from which the image was created.  
  
# 波束形成模块  
* dsb – 延迟求和波束形成器。这个代码里面可选给麦克风加权重。The Delay-Sum Beamformer is the simplest of the beamforming algorithms. This function aligns a group of microphone tracks based on the time difference of arrival of a sound source based on the measured positions of the source and microphones and adds these delayed recordings together. These operations should increase the target signal relative to the interference since the delay operation will bring the target signal components into phase and cause them to add constructively, while the interference sources are likely to be shifted out of phase and thus add destructively. This function also provides an option to weight each microphone with a value inversely proportional to the distance of the microphone from the focal point of the beamformer. This inverse weighting is useful for widely-spread microphones for immersive near-field cases. It has little to no impact on far-field cases.  
  
* gjbf – GSC波束形成器。The Griffiths-Jim Beamformer (also known as the Generalized Sidelobe canceler, or GSC), an improvement that builds on the Delay-Sum beamformer. The GJBF comprises two signal flow paths into one, a DSB approximates the target signal, while in the other path pairs of microphone signals are subtracted and adaptively filtered using LMS filters to approximate the interference. The paths converge by simply subtracting the approximated noise signals from the target. Several enhancements proposed by Hoshuyama et al (“Robust Adaptive Beamforming.” Microphone Arrays : Signal Processing Techniques and Applications. Ed. Michael Brandstein and Darren Ward. New York: Springer, 2001) are also available in this implementation, including adding LMS adaptive filters to the Blocking Matrix (area where the target signal is cancelled, abbreviated BM), constraints on the LMS taps, and SNR estimation for selective adaptation. For more information on these techniques, consult the papers listed in the References section. This function requires bmlms and mclms.  
  
* bmlms – GSC中阻塞矩阵处理Handles computations for the blocking matrix of a GSC beamformer when adaptive filtering in the BM is selected.  
  
* ccafbounds – bmlms的约束。This highly-experimental function generates the explicit coefficient constraints for bmlms.  
  
* mclms – GSC中多输入消除器（MC）的计算。Handles computation for the Multiple-Input Canceler (MC) of a GSC beamformer.  
  
* corrbf – GSC的变种，有效解决了阻塞矩阵中的泄漏。A new variation on the traditional GSC beamformer. The greatest limitation on the GSC’s performance is leakage in the Blocking Matrix, which can cause some target signal cancellation and hamper performance. This algorithm proposes two new ways to handle this problem:  
Instead of taking simple differences between microphone tracks, use the Wiener coefficient (a scalar derived from expected values that minimizes the difference between two signals).  
Instead of using alignments from the Delay-Sum beamformer, calculate the cross-correlation between tracks over a window and shift the tracks to where this correlation is greatest and use this value in the Delay-Sum beamformer subsequently. This modification could make up for errors in microphone and speaker position measurements and could make it possible to track a moving target speaker with automatic target position updates.  
tfmask – Creates and applies time-frequency masks to a group of beamformed signals to further reduce interfering speakers (coherent interference). This function is based on the beamformer having its highest gain at the focal point and the other sound sources being not so loud as to overcome that gain. It then performs a simple time-frequency decomposition and compare power differentials between the speaker of interest and interfering beamformed signals to determine the time frequency region to mask out. This requires the getMsk function.  
  
* getMsk – 从所关注的波束形成的扬声器的短时间频谱和该空间中所有其他重要源的波束形成信号生成所有频率仓的二进制掩码。 如果任何干扰源具有比感兴趣的扬声器更大的功率，则掩蔽特定频率仓。Generates a binary mask for all frequency bins from a short-time spectrum of the beamformed speaker of interest and the beamformed signals of all other significant sources in the space. A particular frequency bin is masked if any interferer has greater power than the speaker of interest. This is the most aggressive masking. The function can be edited to create other rules.  
  
## 演示用例  
* partyanalysis – A test script demonstrating how to use the above m-files to carry out several types of beamforming. This function requires all of the beamforming functions along with micpos.dat, srcpos.dat, and cocktail11k.wav.  
  
# 校准，测量和性能估算功能  
Calibration, Measurement, and Performance Estimation Functions  
  
* rt60est – 估计房间的RT60时间。This function estimates the RT60 time of a room, which is the time required for a steady-state diffuse sound to drop to 60 dB below its maximum. The function requires data recorded from a burst noise sound (preferably white) that has reached steady state in the room and then stopped. Instructions on how to record the sound in the room are given in the documentation of this function. This function requires that at least 20% of the signal at the beginning is the actual noise burst at steady state in the room, and the last 20% (or more) is the noise floor of the room. The program takes a while to estimate the envelope of the decaying sound and to fit a line to it. The slope is then used for the RT60 estimate. This way, if the room has a high noise floor and the decay cannot be measured down to 60 dB, the decaying sound can be picked up before hitting the noise floor and extrapolated from the estimated slope. This function calls a line fit program and an order statistic filter, both of which are included in this mfile and do not need to be loaded separately. If data is recorded over an array of microphones, the RT60 value for each channel is computed and averaged.  
  
* velest – 该函数基于来自具有声源共线布置的系统和两个麦克风之间的已知距离的测量来估计声音的速度。This function estimates the velocity of sound based on a measurement from a system with a collinear arrangement of the sound source and 2 microphones with a known distance between them. It uses the time-domain delay estimator delayesttm to estimate the time delay between the microphones. White noise bursts typically yield the best delay estimates and are recommended for this measurement. This function automatically estimates the window size and a high-pass filter cutoff for processing the sound (these operations can be changed from the defaults through optional input parameters). If the input signal is longer then the window size for the estimate, this function performs repeated estimates in a sliding window fashion to obtain a final result by averaging all velocity estimates from windows corresponding to correlation values greater than 0.4.  
  
## 演示用例  
  
* testrt60p – 此脚本将rt60est函数应用于wave文件rt60exdata.wav中的记录数据。 数据首先记录房间中的稳态噪声突发，并在噪声源关闭后结束。 在这种情况下，混响声音在最响亮的漫反射声音下降60 dB之前会降低到噪声基底以下。 该脚本使用rt60est函数来估计估计RT60时间的衰减声音的斜率。 脚本可能需要一段时间才能在较慢或有限的内存系统上运行（大约一分钟或两分钟）。 大量计算用于使用订单统计过滤器平滑包络。This script applies the rt60est function to the recorded data in wave file rt60exdata.wav. The data starts with a recording of the steady-state noise burst in a room and ends after the noise source has been turned off. In this case the reverberant sound drops below the noise floor before it drops 60 dB from the loudest diffuse sound. This script uses the rt60est function to estimate the slope of the decaying sound from which the RT60 time is estimated. The script may take a while to run on slower or limited memory systems (on the order of a minute or 2). A significant amount of computation is devoted to smoothing out the envelope with order statistics filters.  
  
* testvelest – 此脚本使用velest函数和wav文件sound_speed_p45m.wav中记录的数据。使用共线配置中的1秒白噪声突发记录数据，其中2个麦克风间隔0.45米。该脚本调用velest函数并返回一系列速度估计值，这些速度估计值被平均并计算95％置信度限制。另外，绘制原始麦克风信号以及每个加窗的有效数据段的速度估计和相应的相关系数。请注意，在实践中，此测量中最难的部分是获得麦克风之间的准确距离。在这种情况下，1毫米。测量误差（约2％）可以使速度估计误差为8 m / s。麦克风距离越远，距离测量误差对速度估计误差的影响越小。另一方面，麦克风距离越远，记录越容易受到多径干扰。在进行测量时必须考虑这些因素。This script uses the velest function with recorded data in wav file sound_speed_p45m.wav. The data was recorded using a 1 second white noise burst in a collinear configuration with 2 microphones separated by 0.45 meters. The script calls the velest function and returns a sequence of velocity estimates, which are averaged and the 95% confidence limits are computed. In addition, an original microphone signal is plotted along with the velocity estimates for each windowed valid data segment and the corresponding correlation coefficients. Note that in practice the hardest part of this measurement is obtaining accurate distances between the microphones. In this case, a 1 mm. measurement error (about 2%) can make an 8 m/s error in the velocity estimate. The further apart the microphones are, the less impact the error in distance measurement has on the velocity estimate error. On the other hand, the further apart the microphones are, the more susceptible the recording is to multipath interference. These must be considered when making measurements.  
  
# 语音清晰度估计函数  
* sii – 根据ANSI s3.5-1997标准计算可懂度。This funciton is developed by Hannes Muesh which calculates Intelligibility based on the ANSI s3.5-1997 standard. This function is used from the website http://www.sii.to/index.html which is created by the members of the Acoustical Society of America (ASA) Working Group S3-79, which is in charge of reviewing American National Standard ANSI S3.5-1997.  
  
* intel – 该功能分别输入信号和噪声矢量，将它们分成较小的段，以动态计算它们的频谱电平，用于估算语音清晰度指数的函数sii的输入。This function inputs the signal and noise vectors separately, breaks them into smaller segments to dynamically compute their spectrum levels for inputs to the function sii which estimates the Speech Intelligibility Index.  
  
* spectrumlevel – 该功能基于三分之一倍频程方法将输入信号分成十八个频带，并估算每个频带中的频谱功率电平。This function divides the input signal into eighteen bands based on One-third octave band method and estimates the spectrum power level in each individual band.  
  
* rmsilence – 该功能从语音信号中去除静音间隔并对其进行滤波，以减少来自有效语音段（点击）的串联的失真。  
  
## 演示用例  
  
* testscript_intel – 使用干扰扬声器和白噪声估计单通道语音记录的SII的示例，估计各种信号和噪声水平条件下的语音噪声条件的可懂度This script shows an example of estimating SII of a single channel speech recording with an interfering speaker and white noise. This script estimates the intelligibility of speech-in-noise conditions for various signal and noise level conditions. The script reads two wave files; the first one (man’s voice) is the target signal and the second one (woman’s voice) is the interfering speaker. In order to contrast the effects of an interference speaker (non-stationary noise) with a white noise interference (stationary noise/constant power) a white noise signal is also used and presented sequentially (hit any key to hear next sample). These signals are scaled (varying SNR) to illustrate numbers for good intelligibility (~.6), barely intelligible (~.2), and unintelligible (.1). The output of the script plots the Speech Intelligibility Index over 100 ms. windows that are slid over the speech signal, and displays the computed mean and standard deviation of SII (for active speech, silence intervals were excluded). Users can change the envelope threshold which is used to remove the silence intervals so the mean SII is not as dependent on pauses between words (if speech is not active intelligibility is low). They can also change the length of the overlapping time windows over which the SII is estimated. The scaled target signal together with the interfering signal (noise) is played for reference purpose. It uses the following functions from the Array Toolbox: intel, sii, spectrumlevel, rmsilence, wav2sig and wave files: woman1.wav, man1.wav.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjk1NDkwMDk0XX0=
-->