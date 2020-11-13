# References and EEG Parameters
> By Melanie Furrer

### Sleep EEG recording parameters
We are using high-density (HD) systems for our sleep EEG recordings at the Children’s Hospital Zurich. High-density means that there are many electrodes (more than in the classical setup used in clinics) providing a high spatial resolution. In our case, we are using 128 electrodes. 124 of which are implemented in the EEG-net and include the electrodes used to detect eye movements (EOG). Two are placed on the earlobes (alternative references, see below) and two on the chin muscles (to measure muscle activity, EMG). There are two additional electrodes implemented in the middle of the net, a reference electrode (cz) and a ground electrode (COM) to reduce noise.

![](images\HDnet\Boy_HDEEG.jpg)![](images\HDnet\128channelNet.png)

Since we are measuring voltage, so the difference in electrical potential between two points, we always need a reference to be able to record data. We record our data with a common reference that is located on top of the head (cz, midpoint between the ears and between nasion and inion). All 128 electrodes are referenced to the cz reference electrode, meaning that we measure the difference in electrical potential between each of the 128 electrodes and the reference electrode.

We usually record sleep EEG with a sampling frequency of 500 Hz (500 samples per second).

##Re-referencing data
For certain analysis, another referencing system is needed. Therefore, we re-reference our data according to the type of analysis we want to perform. Re-referencing is performed by a simple subtraction of the signal of two electrodes.

If the two electrodes that are referenced to each other are both on the scalp, the amplitude of your data will be higher the further away the two electrodes are because brain activity will differ more. This effect can be clearly observed in our data if we do not re-reference it, since the distance from each electrode to the common reference differs considerably. There are cases in which this is not a problem and we thus do not need to re-reference our data, one example for this is “artefact-rejection” [so](https://hubersleeplab.github.io/Artifacts.md).
 
###Examples of when to re-reference data

- **Mastoid-referencing for sleep scoring**: For sleep scoring, data is re-referenced to the contralateral mastoids (the bone behind the ears). Specifically, the EEG electrodes used for scoring (according to the Manual for Scoring Sleep) on the right side are re-referenced to the left mastoid and the electrodes on the left side to the right mastoid. Mastoid-referencing will lead to high amplitude data, because the reference electrode is 1st located above a bone (less brain activity in the signal) and 2nd far away from the EEG electrodes. This will make the scoring easier.

- **Average-referencing for power calculations**: If we want to look at the EEG power in a certain frequency range (e.g. slow wave activity), we usually use the average signal of all electrodes to re-reference our data. This is done after channels with low data quality have been excluded to avoid introducing artefacts. In this way, the reference does not have a location which would influence local signal amplitude. This system is thus optimally suited to local changes of power across the scalp.

- **Earlobe referencing**: Referencing your data to the earlobes is very similar to mastoid referencing. Thus, the earlobes can be used as a backup for scoring (in case of bad signal quality of the mastoids). Furthermore, earlobe referenced data is sometimes used to detect slow waves.

- **Bipolar referencing**: In order to determine the muscle tone, the signal from the two EMG electrodes (located above chin muscles) are reference to each other. The same is done to identify eye movements. Two pairs of EOG channels (electrodes located below and above eyes) are referenced to each other (for details see Scoring Manual).
