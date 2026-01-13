INSIGHT

- deep networks are biased towards lower frequency function. Mapping the input to a high dim space helps learning high f variation

QUESTIONS:

- how does the quadrature rule work
- what is stratified sampling and why does it work better and approximating integration over continuous functions
- why is it multi view consistent with the restriction of predicting only density from x
- how do you go from the image to the camera ray representation?

GLOSSARY  
Level sets: set where the functions that take the same value ie ->f(x, y) = z

occupancy field: grid of random binary variable describing the presence of an object.

PSNR: peak signal to noise ratio

= 10 \*log\_10( MAX / mean square error )

MSE = sqrt\*(reconstructed\_image - gt \_image)\*\*2)

SSIM = **structural similarity** **index measure** ( image degradation as perceived change in structural information, while also incorporating important perceptual phenomena, including both [luminance](https://en.wikipedia.org/wiki/Luminance "Luminance") masking and [contrast](https://en.wikipedia.org/wiki/Contrast_(vision) "Contrast (vision)") masking terms. )

formula is based on the combination of luminance, constract and structure, weighted

LPIPS = learned perception image patch similarity  see <https://arxiv.org/pdf/1801.03924> **(L2 distance over the feature of some metric)**