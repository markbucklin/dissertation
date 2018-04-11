**Unique contributions of parvalbumin and cholinergic interneuron
populations in organizing striatal networks during voluntary movement**

**STAR Methods**

Animal Surgery:
---------------

All animal procedures were approved by the Boston University
Institutional Animal Care and Use Committee.  Chat-Cre mice
(B6;129S6-Chat^tm1(cre)Lowl^/J) and PV-cre mice
(B6;129P2-Pvalb^tm1(cre)Arbr^/J), 8--12 week old at the start of the
experiments, both male and female, were used in this study (Jackson
Laboratory; Maine). Mice first underwent surgery for implantation of a
sterilized custom imaging window with an attached guide cannula that was
assembled before surgery. The window/guide assembly consisted of a
stainless steel imaging cannula (OD: 0.317 mm, ID: 0.236 mm, height, 2
mm diameter), fitted with a circular coverslip (size 0; OD: 3mm) adhered
using a UV-curable optical adhesive (Norland Products). The guide
cannula (26 gauge; C135GS4; Plastics, Roanoke, VA) was fixed at a 45°
angle and terminated flush to the base of the imaging window. To access
dorsal striatum, the overlying cortical tissue was carefully aspirated
away to expose the corpus callosum as an anatomical guide. The white
matter was carefully thinned until the underlying striatal tissue could
be visualized via a surgical microscope. The imaging window was then
lowered in place and centered over the dorsal striatum (AP: +0.5, ML:1.8
mm, DV: -1.6). During the same surgery, a custom aluminum head-plate was
attached to the skull anterior to the imaging cannula. Upon complete
recovery (21-28 days after surgery), animals were injected with a 1µL
cocktail containing 500 nL AAV9-Syn-GCaMP6f.WPRE.SV40 (titer: \~6e12
GC/ml??? do we have the exact number on the tube?) and 500 nL
AAV9-CAG-flex-tdTomato.WPRE.SV40 virus(titer: \~6e12 GC/ml) through the
attached guide cannula using a 10uL syringe (701N; Hamilton Company,
Reno, NV) controlled by a microinfusion pump (UltraMicroPump3-4; World
Precision Instruments, Sarasota, FL) fitted with a 33 gauge infusion
cannula (C135IS4; Plastics, Roanoke, VA). The injection occurred at a
speed of 100 nl/min. Both viruses were obtained from the University of
Pennsylvania Vector Core.

**Animal Training:**

*[Animal handling and habituation:]{.underline}*

Animals were allowed to completely recover from surgery (typically about
21-28 days) before being handled and habituated to the imaging/recording
apparatus. Mice were first handled for several days before being
headfixed to the spherical treadmill. Mice were then habituated to
running on the spherical treadmill while headfixed for two weeks, about
3-4 days per week, at the same time of day as subsequent recording
sessions (\~10am-2pm, approximately 8-12 hours after lights-on). Each
animal received at least 10 habituation sessions prior to the first
recording day. Habituation was performed in the dark with the imaging
LED illuminated to the same intensity as it would be for recording
sessions.

A single imaging session took approximately 25 minutes. Prior to the
imaging session animals were positioned underneath the microscope, and
imaged while freely navigating the spherical treadmill. .

**Data Acquisition:**

*[Image Acquisition with sCMOS cameras.]{.underline}*

Image acquisition was performed via custom microscope equipped with a
scientific CMOS (sCMOS) camera (ORCA-Flash4.0 LT Digital CMOS camera
C11440-42U; Hamamatsu, Boston, MA). GCaMP6f fluorescence excitation was
accomplished with a 5W LED (LZ1-00B200, 460 nm; LedEngin, San Jose CA).
tdTomato fluorescence excitation was accomplished with a 1000mA LED
(LXML-PX02-0000, 567 nm; Lumileds, San Jose CA). Custom microscope
included a Leica N Plan 10X 0.25 PH1 microscope objective lens, a dual
band excitation filter (FF01-468/553-25), dichroic mirror
(FF493/574-Di01-25x36), and a dual band emission filter
(FF01-512/630-25; Semrock, Rochester, NY), and a commercial SLR lens
focused to infinity as the tube lens (Nikon Zoom-NIKKOR 80-200mm f/4
AI-s).

A custom MATLAB script was used to generate the timing of data
acquisition, which was then delivered via a I/O interface as TTL pulses
(USB-6259; National Instruments, Austin, TX) to trigger data
acquisition. These TTL pulses triggered image acquisition from the
Hamamatsu sCMOS camera (Cat\#) through the camera software HC Image Live
(HC Image Live; Hamamatsu; Boston, MA). Due to the large size of each
image frame, sampled at 1024\*1024 pixels, the exact sampling intervals
are impacted by the windows operating system. In general, sampling rate
was approximately 20Hz. For each image frame, LEDs were turned and the
exposure time for each image frame was fixed at 20ms, even though the
exact frame rate for each frame may jitter. Each image frame is captured
as multi-page tagged image file format (mpTIFF's). For each animal, we
first recorded GCaMP6f fluorescence for about 10-30 minutes. At the
conclusion of the GCaMP6f imaging session, we recorded tdtomato
fluorescence for \~10 seconds (approximately 50 frames at 200ms
exposure).

Because of the large imaging data size, we collected 2048 image frames
at a time as one video file, stored in computer memory, and then stopped
image acquisition to allow transfer of imaging data from computer memory
to hard-drive.

*[Movement data acquisition ]{.underline}*

These same TTL pulses were also used to trigger data acquisition from
the spherical treadmill. The spherical treadmill was construct following
the design by Damback et al...., which contains a 3D printed holder for
a Styrofoam floated with house air. Two computer mice were affixed to
the side of the Styrofoam ball, approximately at the equator, to read
out the ball movement. Each computer mouse was located 39 degrees away
from the axis of the mouse body on either side of the mouse body. The
data from the computer mice were read by a custom script on a Raspberry
Pi (Vendor Cat\#), and relayed to the computer through Matlab. The x and
y coordinates from each of the computer mouse were saved as mat files,
and then analyzed in Matlab.

$$\frac{\operatorname{}}{\operatorname{}}$$

$$$$

$$\left(^{}^{} \right)^{\frac{}{}}$$

**Ca Imaging Data** **Analysis:**

*[Image Pre-processing: Contrast Enhancement,]{.underline}* *[Motion
Correction]{.underline}* *[and Baseline Subtraction]{.underline}*

Image frames first underwent several pre-processing steps to attenuate
motion artifact, as previously described (Mohammed et al., 2016).
Briefly, we first performed homomorphic filter of each image frame to
enhance contrast both spatially and temporally. We then performed motion
correction through cross-correlation between a given image frame and a
reference frame. The reference frame was updated by sequential addition
of each aligned frame.

We then performed background subtraction using a modified methodology by
Muhammed et al. (2016). Specifically, we first identified the minimum
fluorescence for each pixel across the first video (\~2mins of
recording, XXXX frames) of each session. We then spatially convolved the
minimum fluorescence throughout the whole image field to determine the
background value for each pixel, which was then subtracted from all
frames in the entire imaging session.

To identify pixels with dynamic GCaMP fluorescence changes, we subtract
the fluorescence intensity at each pixel with a "frame-wide baseline
fluorescence" of a given frame. Specifically, we first calculated the
variance of each pixel over time (during the first video), and then
smoothed the variance for each pixel spatially using a spatial Gaussian
filter (). We identified pixels with variance less than the average
variance of all pixels of a given frame. We then calculated the
"frame-wide baseline fluorescence" by averaging the intensity at the
identified pixels.

*[Region of Interest (ROI) identification:]{.underline}*

Semi-automatic image registration algorithms have been developed for ROI
identification in specific brain regions (Cite, Ali's paper). We note
however, these programs are often not yet robust enough to be adapted to
this dataset. Therefore, we developed a manual approach for ROI
identification. After image pre-processing, using the
maximum-minus-minimum fluorescence of each pixel, we generated the
maximum-minus-minimum image frame for each GCaMP (green channel)
recording session. We then manually identified neurons based on their
shape, using a circle with a radius of 6 pixels, corresponding to 7.8
microns).

To identify the PV or CHI cells among the selected ROIs, we overlaid the
identified ROIs onto the images taken in the red channel for tdtamato
visualization. For the red tdtomato video, we first processed the video
in an identical fashion as in the green channel as described in image
pre-processing above, but without background subtraction. Then, for each
image frame, we applied a spatial filter (a square spatial Gaussian
filter of width 5 pixels and a standard deviation of 0.8) to further
smooth the image. We then identified the maximum intensity of each pixel
and calculated the maximum intensity image frame. To facilitate the
identification of cell bodies, we thresholded the red images to reveal
the brightest top 5% pixels. PV cells or CHIs were then identified as
being positive for tdtomato fluorescence on the red image.

*[Trace extraction and Ca fluorescence peak
identification:]{.underline}*

[ΔF/F time series calculation:]{.underline} Fluorescence traces were
extracted for each ROI using a modified version of software from
Mohammad et al. (2016). For each ROI, we calculated as the average
fluorescence intensity across all pixels of a given frame that has been
pre-processed. We then calculated the the average fluorescence (F) of
each ROI across all frames. ΔF/F time series for each ROI were
calculated as the fluorescence at each fame minus the average
fluorescence F, and then divided by the average fluorescence F. Due to
the jitter of data acquisition rate, we interpolated ΔF/F traces so that
consecutive data points were 0.0469 seconds apart using piecewise cubic
polynomial interpolation function (Matlab function: interp1, using the
option 'pchip').

ΔF/F traces were used to calculate....., as shown in Figures
XYZ\>\>\>\>\>\>\>\>

[Ca event identification:]{.underline} as described in the main text,
there are two major types of Ca events with distinct temporal dynamics.
One type is transient, with sharp rising and decay phases, and the other
is slow in rising and long lasting. To identify Ca events, we first
detrended the ΔF/F Ca traces. We smoothed the Ca trace using a moving
average of 21 points (10 data points on either side (0.469 s)), and then
identified the lowest fluorescence value within a radius of 500 data
points (23.5 seconds) and multiplied it by 1.05. We then calculated the
"detrended ΔF/F" by subtracting the original ΔF/F with this
moving-averaged minimum value for each time point as described by Jia et
al (2011).

For transient Ca events, we identified all points (peaks) within each
"detrended ΔF/F" trace with fluorescence exceeding 3 standard deviations
above the mean of the trace. We then recursively performed this step
after removing peak points, until no more peak points were identified.
During each iteration, the values deemed to be the peaks were not
considered. Next, we screened the peaks using an amplitude threshold of
5 standard deviation of the baseline calculated from the data points
that are not deemed as peaks. Continues peak points were then grouped
into potential events. If any potential events contain no data points
above the baseline, that event is not considered as a Ca event.

For slow Ca events that are prevalent in PV cells, the "detrended ΔF/F"
trace was further was smoothed with a Savitsky-Golay filter with an
order 3 polynomial and a frame size of 101 data points (4.74 seconds)
(Matlab function "sgolayfilt"). We then identified all peak points as at
least 2 standard deviations above the mean of the trace. The rest of the
steps are the same as for transient event described above.

Upon manual inspection, we found 1.9% of neurons (23 out of 100,000
events) have both transient and slow Ca events. These neurons present
additional challenge in Ca event identification and were excluded from
further analyses.

Ca events were analyzed for ....., as shown in Figures XYZ...

[Deconvolution of Ca traces]{.underline}

Given that GCaMP6 fluorescence decay is due to the kinetics of the
protein sensor conformational changes, but not directly related to
neural activity, we deconvolved Ca traces to better identify time
periods during which cells are highly active. In order to approximate
these time periods, we labeled only those points corresponding to the
rising phase of an identified peak for each Ca trace as 1s, and labeled
the rest of the trace as 0s.

Deconvolved Ca traces were used for ....calculations as shown in
Figures....XYZ

**[Movement Data Analysis:]{.underline}**

**[Spherical treadmill calibration:]{.underline}** To map the Styrofoam
ball movement to actual mice linear velocity, we first calibrated the
spherical treadmill. We pinned the two sides of the ball at the equator
perpendicular to each of the two computer mice, and then rotated the
ball of a certain physical distance to obtain the translation factor to
translate the computer mouse coordinates to physical distance. The two
computer mouse sensors were calibrated separately. Each computer mouse
sensor was composed of a vertical reading and a lateral reading, and
each reading is also calibrated separately.

**[Linear displacement]{.underline}** **[calculation:]{.underline}** We
calculated animal's linear displacement in two perpendicular directions.
One direction (x-axis of animal movement), is calculated from the
vertical reading of one sensor. The other direction (y-axis of animal
movement) is calculated from the vertical readings of both sensors,
using the following equations:

$$\frac{\operatorname{}}{\operatorname{}}$$

$$$$

Where L is the vertical reading from the left sensor, R is the vertical
reading from the right sensor, and θ is the angle between the two
sensors relative to the center of the ball. To compute the change in
linear distance, we computed: $\left(^{}^{} \right)^{\frac{}{}}$. D is
the change in distance between two readings, where each reading is
triggered by TTL pulses as described above. To compute linear velocity,
we divided the linear distance over time.

We found that X, Y readings were in general smaller than 5cm. In some
sessions, occasionally (\<1%), we found occasionally very large readings
(\>10cm) that are rare and brief (\<1%), which are due to computer
sensor instrument noise. We replaced these data points with null values
before further analysis.

**[Rotational displacement]{.underline}** **[calculation.]{.underline}**
We also calculated animal's rotational displacement, where mice are not
changing their spatial coordinates, but simply circling at the same
spot. In this case, we pinned the ball on the top and the bottom, where
the top corresponds to the location of the mouse's body, and calibrated
the lateral readings from each of the two sensors. To compute the change
in rotational distance, lateral readings from both computer sensors were
converted to radians using the calibration factor, and the results from
the two computer sensors were then averaged. To compute rotational
velocity, we divided the rotational distance over time.

**Data interpolation.** Linear and rotational velocity were interpolated
in the same way as that performed on Ca traces described above.

**Statistics for rotation preference (Fig. 4D).** Rotational velocity
for each session was compared using a circular version of a one-sample
t-test (circ\_mtest) function in the Circular Statistics Toolbox written
for MATLAB [Berens, 2009](#_ENREF_6)(). To test whether or not there was
an overall direction bias, we compared the rotational velocity of each
session to zeros, with the alpha=0.05.

**[Identification of sustained periods of movement with high and low
linear velocity.]{.underline}** We identified periods of high versus low
linear velocity (speed) using a modified method as previously described
[Barbera et al., 2016](#_ENREF_5)(). Briefly, we first smoothed each
linear velocity trace using a low-pass Butterworth filter with a
low-pass frequency of 1.5 Hz, and then identified the time periods at
which the smoothed linear velocity exceeded 5 cm/s for at least 2
seconds. These periods were considered to be periods of high speed.
Similarly, periods during which the smoothed linear velocity of the
mouse stayed below 1 cm/s for at least 2 seconds were considered low
speed periods.

**[Movement onset,]{.underline}** **[offset]{.underline}** **[and peak
identification.]{.underline}** To identify linear velocity onset and
offset, we used the unsmoothed version of the linear velocity trace. We
first thresholded the linear velocity trace using a threshold of 5 cm/s,
and identified all time periods of high velocity. To identify movement
onsets, we first identified the transition point when linear velocity
changed from below 5cm/s to above 5cm/s. We then examined the linear
velocity within 500ms before and 500ms after each transition point. A
movement onset transition is defined as when velocity remained below
5cm/s for at least 500ms before the transition point, and also exceeded
40 cm/s within 500ms after the transition point. The transition points
satisfied these criteria were considered movement onsets.

To identify linear velocity offsets, we first identified the transition
point when linear velocity changed from above 5cm/s to below 5cm/s. We
then examined the linear velocity within 500ms before and 500ms after
each transition point. A movement offset transition is defined as when
velocity exceeded 15 cm/s before the transition point, and also remained
below 5cm/s for at least 500ms after the transition point. The
transition points satisfied these criteria were considered movement
offsets.

Peak-velocity of a movement bout was identified as time points where the
linear velocity exceeded 55 cm/s and the indices to either side of that
time point were lower than it.

To identify rotational onsets, we first calculated the absolute values
of the rotational velocity. We identified the transition point when
rotational velocity changed from below 0.5 radians/s to above 0.5
radians/s. We then examined the linear velocity within 500ms before and
500ms after each transition point. A movement onset transition is
defined as when velocity remained below 0.5 radians/s for at least 500ms
before the transition point, and also exceeded 2 radians/s within 500ms
after the transition point. The transition points satisfied these
criteria were considered rotational onsets.

[Relationship of animal movement and ROI fluorescence]{.underline}

Population movement-triggered fluorescence were computed, by averaging
the ∆F/F traces for each ROI in the +/- 50 time points (totaling about 5
seconds) before and after each movement event across all session.
Statistics were computed using ROI-wise averages for movement-triggered
events and for ROI-triggered velocity (Figs....).

To determine whether or not a neuron was significantly positively or
negatively modulated by a particular type of movement event (as plotted
in Figures 4A, B, C, G, and H), we used one-tailed non-parametric
t-test, the Wilcoxon rank-sum test, to compare the fluorescence values
of the mean fluorescence for each ROI. We compared the 40 data points
(\~2 seconds) before versus after an identified movement onset or
offset. If the respective p-value for positive modulation was \< 0.025
the ROI was considered positively modulated. If the p-value for negative
modulation was \<0.025, the ROI was considered significantly negatively
modulated. Neurons were then assigned to one of the four categories:
speed-only, rotation-only, conjunctive, and neither.

We determined whether or not neurons within the same category tend to
aggregate within close proximity (100um) (plotted in Figures 4B and 4G).
We calculated the proportions of neurons that belong to the same
category of a given neuron versus all neurons within and beyond 100um of
the neuron. These two proportions, within 100um versus beyond 100um,
were compared via a chi-squared test. The same analysis

was used to test the aggregation of neurons that were categorized as
being speed-only, rotation-only, and conjunctive (Fig. 4H).

To determine whether the neurons is more likely to be multi-taskers, or
more likely to be conjunctive than to either speed-only or
rotation-only, we performed chi-square test of the 2X2 contingency
table.

Table:

We determined how neurons of different categories relate to different
aspects of movement, linear velocity, rotational velocity, or linear
acceleration (Figures 3E, 3F, and 4E). For each recording session, we
first identified the time periods with a given absolute linear
velocity(Fig. 3E), absolute rotational velocity (Fig. 4E), or absolute
linear acceleration(Fig. 3F). We then computed the mean ∆F/F of each
neurons within these time periods. ∆F/F of all neurons within a given
neuron type were compared across time periods with different aspects of
movement, using the non-parametric ANOVA, Friedman test.

To evaluate how linear velocity changed around Ca events, we calculated
Ca event-triggered linear velocity changes by aligning to the onset of a
Ca event (Fig. 3G). We then averaged linear velocity for all Ca events
of a given individual neuron. We compared the mean velocity in 500 ms
before versus 500ms after the onset of each Ca event, using the
non-parametric, repeated measures (paired) ANOVA, Friedman test. The
same alignment process and Friedman test were used to compare linear
velocity changes triggered by the Ca events of different cell types. To
compare across cell types, we normalized the mean velocity of a given
cell type by the mean velocity value at the time of Ca onset. If
Friedman test revealed a significant effect over time, we further
performed Kruskal-Wallis test (one-way non-parametric, non-paired ANOVA)
to compare the effect across cell types.

We compared the properties of Ca events during periods of high linear
velocity versus low velocity.

To compute the area under the curve for each Ca event, all points of a
given Ca events (peak points) were baseline subtracted using the mean of
the 20 data points (\~1 second before) before each event onset. If a Ca
event was located closer than 20 data points of anther Ca event or the
beginning of a recording session, we averaged all the data points that
preceded that Ca events but not being part of the previous Ca event. To
better estimate area under curve of transient Ca events, we further
smoothed ∆F/F traces with a 21 point moving average filter (10 points on
either side) for traces containing transient Ca events, but not for
traces with slow Ca events. In order for a Ca event to be included in a
high or low-speed segment for further analysis, the entire event, both
ascending and descending, had to reside in the respective time period.

To compute event height, we identified the maximum fluorescence value of
an event. The onset of an event had to be within a high-speed or
low-speed period in order to be included for further comparison.

To compute Ca events rate across the entire session, we calculated Ca
events per second throughout the entire recording session. To compute Ca
events rate during high versus low movement speed period, we used all Ca
events, as long as any data points within an event were within such a
time period. Ca event properties, area under the curve, and event
height, and events per second, were averaged for each neuron, and the
differences between high- and low-speed time periods were assessed using
a Wilcoxon sign-rank test (non-parametric, paired t-test).

*[Pair-wise correlation analysis between]{.underline}* *[neuron
pairs]{.underline}*:

An asymmetric correlation coefficient was calculated as described
previously using deconvolved Ca traces [Schwartz et al.,
1998](#_ENREF_34)[Barbera et al., 2016](#_ENREF_5)(; ). To compute an
asymmetric correlation coefficient from neuron A to neuron B, the
following equation was used:

$$r_{A \rightarrow B} = \frac{n_{A \cap B}}{n_{A}}$$

That is, the number of binary events (sequences of 1s in deconvolved
traces) in neuron A that overlapped at any point with an event in neuron
B were divided by the total number of events in neuron A. To compute a
single value for the strength of the connection between A and B, we
averaged the correlation coefficients in both directions, A to B and B
to A.

To compute significance for these correlation coefficients, the
deconvolved traces were randomly shifted circularly and uniformly over
the entire length of the trace. Correlation coefficients were recomputed
on these shifted traces to build a surrogate dataset. This process was
repeated 2000 times for each neuron pair in order to generate confidence
intervals. Correlation coefficients with a value that exceeded 95% of
the surrogate dataset were considered significant. For traces with no Ca
events, we used a null value as their correlation coefficient (Figures
5B and 5C), and were considered not significant (Figure S4). For the
false color images showing the spatial distance between correlated
neurons (Fig. S4), the percentage of neuron pairs with significant
correlations were plotted over their anatomical distance. The display of
anatomical clustering in Fig. 5A, we used the [ ]{.underline}
complete-linkage clustering function of matlab
\[f(linkage)...XYZ...169...\] for this particular recording session
35???? clusters were used.

We also compared pairwise correlation coefficients between neuron pairs
during periods of high versus low speed (Fig. S3). Because of the
sparseness of Ca events, we here used ΔF/F values and Pearson's
correlation instead of the asymmetric correlation described above.
During each specified time period, the correlation coefficients were
determined between each pair of neurons within the same class, MSN-MSN
pairs, CHI-CHI pairs, and PV-PV pairs. These values were merged together
and then compared between low verus high speed period, using Sign-rank
test (non-parametric, paired ttest).

*[Calculation of predictor performance using]{.underline}* [* regression
analysis:*]{.underline}

To estimate how each cell type predicted movement or population SPN
activity (Fig. 6). We built a linear model and used regression analysis
to determine the predictor performance. Regressions are quantified using
10-fold cross-validation(Hastie et al., 2009). Briefly, for each
session, the data are equally divided into 10 segments. Parameters for
each set of features are determined using 9 of these segments, and then
the values for the last segment are predicted using these parameters.
The Pearson correlation coefficient between the predicted and actual
value of this last segment were determined. This process is repeated 10
times, and average correlation coefficients are used for each session.
∆F/F traces, or movement parameters were first binned in intervals of
100 ms, taking the mean value within each bin.

To predict MSN population fluorescence (response variable) (Fig. 6C, D)
using predictors (movement speed, rotation, or a small number of MSNs or
interneurons), we used population MSN fluorescence as the response
variable. Since the number of interneurons are drastically smaller than
the MSNs in any given recording session, we used a random subsample of
MSNs equal to the number of interneurons in that session as predictors.
To better estimate the predictor performance of MSN subpopulations, this
process was repeated 2000 times for MSNs predictors, and the average
value used as the predictor performace for each session. For each
iteration, the selected MSN subpopulations used as the predictor were
subtract from the whole MSN population response variable. The intercept
term was also included in each model.

To predict linear velocity (response variable) using a single MSN, PV,
CHI, or multiple or whole population of MSNs, PVs and CHIs (Fig. 6A, B),
we used linear velocity as the response variable. Re-state the ones
above...XYZ...

Linear regressions were then constructed instead using the mouse's
linear speed as the response variable. Model fit was again assessed with
10-fold cross-validation, as described above. Data were binned into 100
ms intervals and ∆F/F and an intercept term were used as features. For
individual neurons, the ΔF/F for each given neuron was used to construct
its features. Average correlation coefficients between predicted and
actual responses were determined for each individual interneuron, and
the results were then averaged for each session. When examining
population interneuron fluorescence from a given recording session, the
ΔF/F traces for each interneuron were summed across the whole session,
and correlation coefficients for each of the k predictions were
averaged. Finally, for MSN sub-population comparisons, a number of MSNs
equal to the number of FSIs or CHIs in each session were selected at
random with replacement and added to construct a corresponding feature.
This which was combined with an intercept and then likewise regressed
against the speed of the mouse in that session. This random selection
was repeated 2000 times, and the mean correlation coefficients
determined via 10-fold cross-validation were averaged to determine the
mean session correlation coefficient.

***[ROI-triggered fluorescence and probability analyses]{.underline}***

We next wanted to determine the likelihood that a particular type of ROI
was active around the time that another type of ROI fired. As with the
ROI-triggered velocity analysis, events were determined for each ROI by
finding the time point immediately preceding the first time point of the
peak. First we computed pairwise-fluorescence values. For interneurons,
we found the fluorescence values of each MSN around every time that an
interneuron fired, giving us a number of fluorescence values in each
session equal to the number of total interneuron events times the number
of MSNs. For MSNs, we took each of the events in a given MSN, and found
fluorescence values in every other MSN around each of these events,
giving us a number of fluorescence values equal to the total number of
MSN events in all MSNs times the number of MSNs minus 1. For each
fluorescence value, we computed the mean value during the \~1/2 second
prior to the event (10 data points) and the mean value during the \~1/2
second following the event. In order to compare the fluorescence between
the triggering cell types. In order to determine the mean and standard
error of the mean of the fluorescence over the entire \~5 second
interval plotted in Figures 7ai and 7bi, Welford's algorithm was used
for online-estimation given the large size of the data set (B. P.
Welford (1962).\"Note on a method for calculating corrected sums of
squares and products\". Technometrics 4(3):419--420.)

In order to compute ROI-triggered probability, a similar analysis was
performed using the deconvolved calcium traces. For each peak for each
interneuron, the number of MSNs that were active around that peak out of
the total number of possible MSNs active around that peak were stored.
For MSN-triggered MSN probability, the number of other MSNs active out
of the total number of other MSNs were stored. Thus, the probability of
an MSN being active around the time of the peak onset of another MSN was
computed as the number of MSNs active over the total possible number of
active MSNs. We have total possible numbers of coactive MSNs equal to
the number of total fluorescence values detailed in the previous
section. In order to compute a statistic to compare responses between
cell types, the proportions and estimated standard errors at the two
time points following time point t=0 were combined, and z-tests were
performed comparing proportions between each of the cell types.

In order to compute ROI-triggered synchrony, a similar procedure was
performed to activity. However, at the beginning of each peak, the total
number of possible pairs of active MSNs were obtained, as well as the
total number of possible pairs of all MSNs. These were computed as:

$$n_{\text{active\ pairs}} = \frac{n_{\text{MSNs\ active}}\left( n_{\text{MSNs\ active}} - 1 \right)}{2}$$

and

$$n_{\text{total\ pairs}} = \frac{n_{\text{MSNs\ total}}\left( n_{\text{MSNs\ total}} - 1 \right)}{2}$$

As with the ROI-triggered probability analysis, a proportions of active
pairs at the two time points (\~100 ms) after time point zero were
averaged along with their estimated standard errors, and this value was
compared across neuron types.

*[Synchronization analysis:]{.underline}*

Synchronization was defined as the proportion of MSNs simultaneously
active. To detect synchronization peaks, the deconvolved traces for MSNs
in each session were summed, and periods of time during which the summed
activity exceeded 2 standard deviations above the mean were acquired.
The maximum synchronization value in each of period of time was taken to
be a point of peak synchrony. Velocity was determined around each of
these points, and the resulting velocities were analyzed event-wise via
a Friedman test.

*[Statistical Tests:]{.underline}*

In general, we used wilcoxon rank-sum tests, Wilcoxon signed-rank tests,
Kruskall-Wallis tests, Friedman tests, Pearson's Chi-squared test, and
Pearson's correlation were used in these analyses. If the expected value
of any cell in a contingency table used for a Chi-squared test was less
than 5, Yates's correction was used. All tests were two-sided except for
chi-squared tests, which were one-sided. Where this correction was used,
it was noted in the manuscript. For plots that show a colored error bar,
the Matlab package shadedErrorBar was used
(https://www.mathworks.com/matlabcentral/fileexchange/26311-raacampbell-shadederrorbar).
The detailed statistical tests are described above in related analysis.
