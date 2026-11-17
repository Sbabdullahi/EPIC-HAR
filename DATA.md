# Datasets

Neither dataset is redistributed in this repository.

## HHAR (Heterogeneity Activity Recognition)

Stisen et al., "Smart devices are different: assessing and mitigating mobile sensing heterogeneities for activity
recognition", SenSys 2015. Available from the UCI Machine Learning Repository (dataset 344) under CC BY 4.0.
The notebook downloads and unpacks it automatically (Cell 2b, `fetch_hhar`). On Kaggle, switch Internet on.

## LMDHG (Leap Motion Dynamic Hand Gestures)

Boulahia et al., "Dynamic hand gesture recognition based on 3D pattern assembled trajectories", IPTA 2017.
Request the data from the dataset authors or at https://www-shadoc.irisa.fr/english-leap-motion-dynamic-hand-gesture-lmdhg-database/. Place the 50 `DataFile*.mat` files either in
`/content/drive/MyDrive/` (Colab with Google Drive) or provide `LMDHG.zip` at
`/content/drive/MyDrive/`; Cell 2b finds either. Folds are grouped by sequence file.
