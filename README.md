# Thesis

Analisi delle architetture seguenti:

  VAE Classici: https://arxiv.org/abs/1906.02691 (eventualmente Beta-VAE, che son praticamente la stessa rete: https://openreview.net/references/pdf?id=Sy2fzU9gl)
  
  Two-Stage VAE: https://arxiv.org/abs/1903.05789
  
  Deterministic VAE (RAE): https://arxiv.org/abs/1903.12436
  
  DRAW: https://arxiv.org/abs/1502.04623
  
  InfoVAE: https://arxiv.org/abs/1706.02262
  
  [opzionali: 
  WAE: https://arxiv.org/abs/1711.01558
  
  VQVAE: https://arxiv.org/abs/1711.00937]
  
La mia idea è quella di seguire le linee dell'indagine fatta su Deterministic VAE, nell'appendice ha un'analisi bella e fatta molto bene che confronta alcune tipologie di RAE (VAE Regolarizzati introdotti nel paper Deterministic VAE) con diversi regolarizzatori, VAE classici, WAE e altre architetture. 
Nel suo caso l'indagine viene fatta soltanto su VAE non ricorrenti, e su pochissime architetture diverse. Io estenderei quell'analisi in maniera più completa, misurando la qualità delle reti su due fronti:

  Capacità dell'Encoder di recuperare la prior p(z) [misure effettuate con diverse metriche, si visuali che di Moment Matching / MMD]
  
  Capacità del Decoder di generare immagini di alta qualità [misurata con FID o Inception Distance]

A queste poi dipendentemente dai risultati ottenuti posso pensare di aggiungere altre metriche, più che altro per rimuovere il bias (che secondo me è fattore dominante nella maggior parte degli articoli) che spingono il produttore dell'articolo ad utilizzare metriche che avvantaggiano molto la sua architettura, permettendogli di "venderla" come ottima (ad esempio, InfoVAE ben regolarizzato non raggiungerà mai la qualità generativa di DRAW, però ha un Matching del prior molto migliore, perché quello è il suo principale task).

Ovviamente, questa analisi sarà svolta su almeno i seguenti 3 dataset:

  Mnist (o FashonMnist, che però a me non piace particolarmente)
  
  Cifar10
  
  ImageNet (sperando di riuscire a reggerlo con il training)

Mi piacerebbe inoltre anche stampare i risultati ottenuti per quanto riguarda l'interpolation nel latent space e il feature learning (studiare quanto ha imparato l'autoencoder a separare le feature dell'immagine, spostandomi lungo una direzione dello spazio latente e verificando a quale feature corrisponde quella direzione), cosa che vedo fare in quasi tutti i paper, ma non so se a livello di programmazione è una cosa semplice da fare (e quindi posso provare ad aggiungerla) oppure è troppo difficile.
