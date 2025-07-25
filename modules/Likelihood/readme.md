# Likelihood Detector Configuration Files

This readme file is provided to explain the included configuration files for the PAMGUARD likelihood detector (LD). They are provided as examples of how to configure the system and could be used as a basis for creating custom configurations and .psf files.

Contents:

1.  General
2.  Beaked_LD.tcf
3.  Bowhead_LD.tcf
4.  Humpback_LD.tcf
5.  Sperm_LD.tcf

## General

Rather than try to provide a .psf file, users are left to create an appropriate one for themselves, or use one from the PAMGUARD guardians. From here, the PAMGUARD tutorial or online help will demonstrate how to add a LD module and set the basic configuration.

The included .tcf (target configuration files) can be directly imported into the PAMGUARD likelihood detector module. See the online help for this module for the import procedure. After import, users may need to adjust detection band frequencies to compensate for varying bandwidth of their sound source. The bandwidth required for each configuration file is noted below. Other settings should remain valid, but this can be verified by opening the configuration and looking for red bars over a configuration option. A yellow bar indicates a warning, which would cause more than normally expected resources (memory and/or processing power) to be used. This is further explained in the online help.

Users will also need to right click each spectrogram display and enable overlays for each target of interest when they change the LD configuration.

Each example provides some hint of special cases where the overall 'rules of thumb' were not followed in the past. Selecting rules of thumb for all data is near impossible. Hopefully these examples will help expert users better understand the detection module and learn how to best configure it. Even the examples contained herein are likely to be improved as more experience is gained over a broader range of data.

Any questions or comments can be directed to the Principal Investigator for the module (Joe Hood - [jhood\@akoostix.com](mailto:jhood@akoostix.com){.email}) or the current PAMGUARD support team.

## Beaked_LD.tcf

This configuration file provides an example of how to detect beaked whale clicks. It was created to detect beaked whales on the AUTEC range sensed using wideband sonobuoys. It produced over 90% detection rate with only a few false alarms on this data, but may need to be tweaked for other situations.

The example requires at least 35 kHz data (70 kHz sample rate) to run. The minimum time between detections was set to 0.25 seconds as the inter-click interval was \~0.3 seconds.

The signal and guard band frequencies are a bit different than is normally expected for this species (Blainville's Beak Whale) and may need to be adjusted for other cases.

Note that the noise window is longer than recommended by the 'rules of thumb' in the help. This is to provide better averaging, but will allow medium duration signals to be detected. It was tested with windows as short as 2.5 ms and still performed 'OK'. More testing is required to decide on the most robust setting.

## Bowhead_LD.tcf

This configuration file provides an example of how to detect Bowhead whale end notes. It was created using the example data provided by Mobysound (mobysound.org).

The example requires at least 1.5 kHz data (3 kHz sample rate) to run.

Note that the noise window is shorter than recommended by the 'rules of thumb' in the help. This was to avoid bringing neighbouring calls into the noise estimate. The threshold was also lowered slightly from the default (4.0 dB vice 7.0 dB) to detect more calls. More testing would be required to decide on the most robust setting.

## Humpback_LD.tcf

This configuration file provides an example of how to detect Humpback song. It was created using the example data provided by Mobysound (mobysound.org).

The example requires at least 1.5 kHz data (3 kHz sample rate) to run.

Note that the noise window is shorter than recommended by the 'rules of thumb' in the help. This was to avoid bringing neighbouring calls into the noise estimate.

Here two signal bands were established to cover two bands containing several types of units ( a Humpback song unit is like a word in a song). The configuration is tuned to a particular bandwidth and unit duration, with the guard bands helping to ensure that the sound is band limited, reducing false alarms. Note that the unit1 configuration is very similar to the Bowhead end note configuration and will also detect endnotes.

## Sperm_LD.tcf

This configuration file provides an example of how to detect Sperm Whale clicks. It was created using wideband sonobuoy recordings from the AUTEC range.

The example requires at least 35 kHz data (70 kHz sample rate) to run. The minimum time between detections was set to 0.5 seconds as the inter-click interval was just less than a second.

Sperm whale clicks are so broadband that they make use of a standard guard band impossible. Instead, the guard band was used to define what effectively becomes a second noise window (but using the signal window parameter in the guard band; 0.5 seconds). This helps to ensure that signal excess is obtained over both a short and longer term average.
