# Gatorsense hsitoolkit signature detectors Python version
Review and references for many of these signature detectors can be found in the literature review in Taylor Glenn's Ph.D. thesis:
Glenn, Taylor C. Context-dependent detection in hyperspectral imagery. Diss. University of Florida, 2013.

Contact: Alina Zare, azare@ufl.edu

## Inputs:
Each function takes similar inputs starting with hyperspectral image, target signatures, an optional mask (if you want to exclude pixels from analysis). Some functions require other inputs such as mean or background covariance.

## Demo:
This repo contains a demo (demo_signature_det.py) and hyperspectral image (an_hsi_img_for_tgt_det_demo.mat) to run all signature detectors that are available. The demo will calculate all the signature detectors and display them together for the user.

## Current suite of signature detectors:
- abd_detector: Abundance of target signature when unmixed using target signature and background endmembers assuming the linear mixing model
- ace_detector: Squared Adaptive Cosine/Coherence Estimator (Squared ACE), cosine of vector angle between target and pixel spectra after whitening based on background statistics, squared
- ace_local_detector: Adaptive Cosine/Coherence Estimator where background statistics are estimated from local window
- ace_ss_detector: Squared Adaptive Cosine/Coherence Estimator Subspace Formulation
- ace_rt_detector: Adaptive Cosine/Coherence Estimator (ACE), cosine of vector angle between target and pixel spectra after whitening based on background statistics
- ace_rt_max_detector: ACE given multiple target signatures. Confidence value for each pixel is max ACE score over all target signatures.
- amsd_detector: Adaptive Matched Subspace Detector
- ccmf_detector: Class Conditional Matched Filter, Segment data using a Gaussian Mixture Model and then apply SMF to each component
- cem_detector: Constrained Energy Minimization Detector
- ctmf_detector: Cluster Tuned Matched Filter
- fam_statistic: False Alarm Mitigation Statistic
- ha_detector: Hybrid Abundance Detector, unmix using background endmembers as well as using background and target endmembers, model proportions with a Gaussian mixture, compute pixel-wise likelihood ratios
- hsd_detector: Likelihood ratio after unmixing with background and unmixing with background and target signature (Broadwater and Chellappa's method)
- hsd_local_detector: Hybrid Structured Detector using local background estimation
- hua_detector: Hybrid Unstructured Abundance Detector
- osp_detector: Orthogonal Subspace Projection Detector
- palm_detector: Pairwise Adaptive Linear Matched Filter
- sam_detector: Spectral Angle Mapper, calculates vector angle between target signature and each pixel spectrum
- smf_detector: Spectral Matched Filter, inner product between target and pixel spectra after whitening based on background statistics
- smf_local_detector: Spectral Matched Filter using local background statistics
- smf_max_detector: Spectral Matched Filter given multiple target signatures. Confidence value for each pixel is max SMF score over all target signatures.

## Suite of signature detectors under development:
- ftmf_statistic: Finite Target Matched Filter
- mtmf_statistic: Mixture Tuned Matched Filter Infeasibility Statistic
- qmf_detector: Quadratic Spectral Matched Filter
- spsmf_detector: Subpixel Spectral Matched Filter

## Suite of signature detectors to be implemented (these use Quadratic programming active set method):
- hs_detector: Hybrid Subpixel Detector
- hsa_detector: Hybrid Structured/Abundance Detector
- hud_detector: Hybrid Unstructured Detector (Broadwater and Chellappa's method)

## Segmented Mode
Signature detectors can also be ran in *Segmented* mode with util/img_seg.py as shown in the demo script.
Segmented mode is where a detector is applied to segments of the imagery separately (i.e., background statistics computed from segment rather than full image).
