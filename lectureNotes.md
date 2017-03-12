2. The Speech Signal

   a brief overview of the phonetic representation of speech and an introduction to models for the production of the speech

   1. Phonetic Representation of Speech

      for most languages the number of phonemes is between 32 and 64.

   2. Models for Speech Production

      ![Schematic model of the vocal tract system ](/images/Schematic model of the vocal tract system .PNG)

      *Voiced Sounds* ( vowels,liquids,glides, nasals) : produced when the vocal tract tube is excited by pulses of air pressure resulting from quasi-periodic opening and closing of the glottal orifice.

      *Unvoiced Sounds* (fricative): produced by creating a constriction somewhere in the vocal tract tube and forcing air through that constriction, there by creating turbulent air flow, which acts as a random noise excitation of the vocal tract tube.

      *Source/System model for speech production*

      ![speech produciton](/images/speechProduction.PNG)

      ​

      - the discrete-time *time-varing* linear system on the right simulates the frequency shaping of the vocal tract tube and provides spectral shaping (often referred to as the specturm envelope). 

      - the excitation generator on the left simulates the different models of sound generation in the vocal tract and provides the basic temporal fine structure. voiced excitation is periodic.

      - samples of a speech signal are assumed to be the output of the time-varing linear system.

      - the short-time frequency response of the linear system simulates the frequency shaping of the vocal tract system.( Since the vocal tract changes shape relatively slowly, it is reasonable to assume that the linear system response does not vary over time intervals on the order of 10ms or so.
        $$
        H(z) =  \frac{\sum_{k = 0}^M b_k z^{-k}}{1-\sum_{k = 1}^N a_k z^{-k}} = \frac{b_0 \prod_{k = 1}^M (1-d_k z^{-1})}{ \prod_{k = 1}^N (1-c_k z^{-1})}
        $$

        - the filter coefficients $a_k$ and $b_k$(labeled as vocal tract parameters) changed at a rate on the order of 50-100 times/s. 
        - Some of the poles ($c_k$) of the system function lie close to the unit circle and create resonances to model the format frequencies. 

      - the fundatmental frequency of the glottal excitatino determines the perceived *pitch* of the voice.

      ​

3.  Hearing and Auditory Perception

   the perception side of the speech chain to discuss properties of human sound perception that can be employed to create digital representations of the speech signal that are perceptually robust.

   1.  The Human Ear

      - outer ear : pinna(耳廓, gathering sound and conducting it through the external canal(外耳道) to the middle ear) 
      - middle ear : tympanic membrane(鼓膜) ,  eardrum(中耳，performing a transduction from acoustic waves to mechanical pressure waves， including three small bones: the malleus锤骨, the incus 砧骨, the stapes 镫骨)
      - inner ear : consisting of the cochlea(耳蜗) and the set of neural connections to the auditory nerve, which conducts the neural signals to the brain. The basilar membrane inside the cochlea vibrates in a frequency-selective manner along its extent and thereby performs a rough (non-uniform) spectural analysis of the sound. 

      ![humanEar](/images/humanEar.PNG)

      Schematic model of the auditory mechanism :

      ![](/images/auditoryMechanism.PNG)

      ​

   2. Percetion of Loudness

      the perception of loudness is frequency-dependent.

      ![](/images/LoudnessLevel.PNG)

      ​

   3. Critical Bands

      The non-uniform frequency analysis performed by the basilar membrane can be thought of as equivalent to that of a set of bandpass filters whose frequency responses become increasingly broad with incerasing frequency.

      Schematic representation of bandpass filters according to the critical band theory of hearing :

      ![](/images/filterBanks.PNG)

      $f_c$ : center frequency ; $\Delta f_c $ : bandwidth.

      $f_c \le 500Hz$ , $\Delta f_c \approx 500Hz$ ; $f_c > 100Hz$ , $\Delta f_c \approx 0.20f_c$

      An equation that fits empirical measurements over the auditory range is 
      $$
      \Delta f_c = 25 + 75[1 + 1.4(f_c/100)^2]^{0.69}
      $$
      $0-20kHz$ 大约有*$25$*个*critical band filters*.

       

   4. Pitch Perception

      voiced sounds and musical sounds have a periodic structure when viewed over short time intervals.

      Relation between subjective pitch and frequecy of a pure tone:

      ![](/images/pitch.PNG)

      横坐标: nonlinear frequency scale, called the mel-scale

      the relation of the pitch and frequency of a pure tone can be approximated by the equation:
      $$
      Pitch \ in \ mels = 1127log_e(1+f/700)
      $$
      $f = 10^3Hz$,$pitch = 10^3 mels$ (人为设定的)

      $f < 10^3Hz$, proportional ; $f > 10^3Hz$, the relationship is nonliear.

      *one critical bandwidth corresponds to about $100 \ mels$ on the pitch scale.( more or less independently of the center frequency of the band)*  

      *pitch period* : the fundamental period of the voiced speech signal.

      ​

   5. Auditory Masking

      masking *occurs* when one sound makes a second superimposed sound inaudible.

      ​

4. Short-Time Analysis of Speech

   Voiced/unvoiced/system model for a speech signal:

   ![](/images/speechSignal.PNG)

   - the unvoiced excitation is assumed to be a random noise sequence, and the voiced excitation is assumed to be a periodic impulse train with impulses spaced by the pitch period ($P_0$) rounded to the nearest sample.

   ​