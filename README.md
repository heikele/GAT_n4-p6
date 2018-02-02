# N400-P600 GAT Decoding of semantic anomalies using EEG

### preprocessing-ICA-Autoreject: script for preprocessing the recorded subject vhdr files, correcting for ICA and auto-rejection and repair
 - creates raw files, ICA files and the autorejection file for subjects.
 

make_epochs: script for epoching the data
 - takes the original events and identifies the onset of the sentence and recreates the events file so that triggers index target word onsets.
 - epochs the data into -300 to 1300 ms relative to target word onset
 - applies ICA correction
 - saves epoched data
        
ERPs: script for ERP analysis
- plots butterfly plot, averaged ROI (left/right anterior/posterior) ERPs for congruent and incongruent trials with 95% bootstrapped variance corridors and topographies for incongruent-congruent trials
- creates a massive dataframe of epoch data over subjects
- creates and saves two separate csvs for N400 and P600 for 2x2x2 anova (congruent/incongruent, anterior/posterior, left/right)


MVPA: script for MVPA analysis
- creates machine learning pipeline (works for Ridge Classifier, Logistic Regression, linear SVM, and non-linear (RBF) SVM).
- investigates how well patterns from 300-500ms (N400) and 600-800ms (P600) generalize over time.
- identifies time points of significant decoding performance (above and below chance - FDR corrected, p<0.05 and p<0.01).
- plots the GAT matrix masked by significance (Threshold Free Cluster Enhancement - p<0.01), diaogonal decoding performance (trained and tested at same time points - masked for significance p<0.05 [thin lines] and p<0.01 [thick lines], FDR corrected), component generalization (N400 and P600 classifier generalization over time - masked for significance p<0.05 [thin lines] and p<0.01 [thick lines], FDR corrected) and difference between classifier performances (P600-N400 decoding accuracy) to identify time points where one classifier performed better than the other (below 0% for N400 better than P600 and above 0% P600 better than N400) and masked for significance (p<0.05 [thin lines] and p<0.01 [thick lines], FDR corrected) 
