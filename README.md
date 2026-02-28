# Eigenportfolio Construction via Random Matrix Theory

# Overview
This project explores the application of Random Matrix Theory (RMT) as a mathematical framework for improving the quality of financial covariance matrices — a critical component in modern portfolio construction and risk management. In practice, when we estimate a covariance matrix from historical asset returns, the result is almost always contaminated with statistical noise. This noise arises because the number of assets being analyzed often approaches or exceeds the number of observations available, making it difficult to distinguish genuine correlations between assets from those that are purely coincidental. Acting on these spurious correlations can lead to poorly constructed portfolios that appear optimal on paper but perform unpredictably in the real world.

Random Matrix Theory addresses this challenge by providing a theoretical benchmark — known as the Marchenko-Pastur distribution — that describes what the eigenvalue spectrum of a purely random matrix should look like. By comparing the eigenvalues of an empirical covariance matrix against this benchmark, we can statistically identify which components of the matrix carry true financial signal and which are simply noise. Eigenvalues that fall within the theoretical random range are treated as uninformative and filtered out, while those that exceed it are retained as meaningful.

From the cleaned, noise-filtered covariance matrix, the project then constructs eigenportfolios — portfolios derived from the eigenvectors associated with the significant eigenvalues. Unlike conventionally weighted portfolios, eigenportfolios are orthogonal to one another and represent independent sources of financial risk and return. This makes them far more statistically robust, as their composition is grounded in genuine market structure rather than artifacts of limited data.
The significance of this work lies in its practical impact on portfolio optimization. Noise in covariance matrices is a well-documented source of instability in methods like Markowitz mean-variance optimization, often leading to extreme, unstable portfolio weights. By applying RMT-based filtering, this project demonstrates a principled and mathematically rigorous way to construct portfolios that are more stable, more interpretable, and better suited to out-of-sample performance.

# Key Concepts:
Empirical Covariance Matrix: Estimated from finite historical returns data. Contains both signal and noise.
Marchenko-Pastur Distribution: The theoretical eigenvalue distribution of a pure random (Wishart) matrix. Acts as a "noise benchmark".
Eigenportfolios: Portfolios formed from eigenvectors of the covariance matrix. Each eigenvector defines an uncorrelated risk factor.
RMT Filtering: Eigenvalues within the Marchenko-Pastur bounds are considered noise; those above the upper bound carry genuine market signal.

# Workflow:
1. Simulate realistic correlated returns (or load real data)
2. Compute the empirical correlation matrix
3. Derive the Marchenko-Pastur distribution and overlay it on the empirical spectrum
4. Filter the covariance matrix using RMT
5. Construct eigenportfolios from the filtered matrix
6. Analyze portfolio turnover over rolling windows
