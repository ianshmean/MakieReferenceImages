## Fractional Brownian surface

```@raw html
<pre class='hljl'>
<span class='hljl-t'>
</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>SparseArrays</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>LinearAlgebra</span><span class='hljl-t'>

</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>AbstractPlotting</span><span class='hljl-t'>

</span><span class='hljl-s'>&quot;This example was provided by Moritz Schauer (@mschauer).&quot;</span><span class='hljl-t'>

</span><span class='hljl-cm'>#=
Define the precision matrix (inverse covariance matrix)
for the Gaussian noise matrix.  It approximately coincides
with the Laplacian of the 2d grid or the graph representing
the neighborhood relation of pixels in the picture,
https://en.wikipedia.org/wiki/Laplacian_matrix
=#</span><span class='hljl-t'>
</span><span class='hljl-k'>function</span><span class='hljl-t'> </span><span class='hljl-nf'>gridlaplacian</span><span class='hljl-p'>(</span><span class='hljl-n'>m</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>n</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-n'>S</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>sparse</span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.0</span><span class='hljl-n'>I</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>n</span><span class='hljl-oB'>*</span><span class='hljl-n'>m</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>n</span><span class='hljl-oB'>*</span><span class='hljl-n'>m</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-n'>linear</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>LinearIndices</span><span class='hljl-p'>((</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-n'>m</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-n'>n</span><span class='hljl-p'>))</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-n'>m</span><span class='hljl-t'>
        </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-n'>n</span><span class='hljl-t'>
            </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>i2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j2</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-p'>((</span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>i</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>))</span><span class='hljl-t'>
                </span><span class='hljl-k'>if</span><span class='hljl-t'> </span><span class='hljl-n'>i2</span><span class='hljl-t'> </span><span class='hljl-oB'>&lt;=</span><span class='hljl-t'> </span><span class='hljl-n'>m</span><span class='hljl-t'> </span><span class='hljl-oB'>&amp;&amp;</span><span class='hljl-t'> </span><span class='hljl-n'>j2</span><span class='hljl-t'> </span><span class='hljl-oB'>&lt;=</span><span class='hljl-t'> </span><span class='hljl-n'>n</span><span class='hljl-t'>
                    </span><span class='hljl-n'>S</span><span class='hljl-p'>[</span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j2</span><span class='hljl-p'>]]</span><span class='hljl-t'> </span><span class='hljl-oB'>-=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-t'>
                    </span><span class='hljl-n'>S</span><span class='hljl-p'>[</span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j2</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-p'>]]</span><span class='hljl-t'> </span><span class='hljl-oB'>-=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-t'>
                    </span><span class='hljl-n'>S</span><span class='hljl-p'>[</span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-p'>]]</span><span class='hljl-t'> </span><span class='hljl-oB'>+=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-t'>
                    </span><span class='hljl-n'>S</span><span class='hljl-p'>[</span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j2</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-n'>linear</span><span class='hljl-p'>[</span><span class='hljl-n'>i2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j2</span><span class='hljl-p'>]]</span><span class='hljl-t'> </span><span class='hljl-oB'>+=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-t'>
                </span><span class='hljl-k'>end</span><span class='hljl-t'>
            </span><span class='hljl-k'>end</span><span class='hljl-t'>
        </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>return</span><span class='hljl-t'> </span><span class='hljl-n'>S</span><span class='hljl-t'>
</span><span class='hljl-k'>end</span><span class='hljl-t'>

</span><span class='hljl-cs'># d is used to denote the size of the data</span><span class='hljl-t'>
</span><span class='hljl-n'>d</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>150</span><span class='hljl-t'>

 </span><span class='hljl-cs'># Sample centered Gaussian noise with the right correlation by the method</span><span class='hljl-t'>
 </span><span class='hljl-cs'># based on the Cholesky decomposition of the precision matrix</span><span class='hljl-t'>
</span><span class='hljl-n'>data</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.1</span><span class='hljl-nf'>randn</span><span class='hljl-p'>(</span><span class='hljl-n'>d</span><span class='hljl-p'>,</span><span class='hljl-n'>d</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-t'> </span><span class='hljl-nf'>reshape</span><span class='hljl-p'>(</span><span class='hljl-t'>
        </span><span class='hljl-nf'>cholesky</span><span class='hljl-p'>(</span><span class='hljl-nf'>gridlaplacian</span><span class='hljl-p'>(</span><span class='hljl-n'>d</span><span class='hljl-p'>,</span><span class='hljl-n'>d</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.003</span><span class='hljl-n'>I</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>\</span><span class='hljl-t'> </span><span class='hljl-nf'>randn</span><span class='hljl-p'>(</span><span class='hljl-n'>d</span><span class='hljl-oB'>*</span><span class='hljl-n'>d</span><span class='hljl-p'>),</span><span class='hljl-t'>
        </span><span class='hljl-n'>d</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>d</span><span class='hljl-t'>
</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-nf'>surface</span><span class='hljl-p'>(</span><span class='hljl-n'>data</span><span class='hljl-p'>;</span><span class='hljl-t'> </span><span class='hljl-n'>shading</span><span class='hljl-oB'>=</span><span class='hljl-kc'>false</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>show_axis</span><span class='hljl-oB'>=</span><span class='hljl-kc'>false</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>colormap</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:deep</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//fractional_brownian_surface/media/image.png" alt="">

    </p>
</div>

```
