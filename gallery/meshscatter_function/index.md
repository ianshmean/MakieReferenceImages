## Meshscatter Function

```@raw html
<pre class='hljl'>
<span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>Makie</span><span class='hljl-t'>
 </span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>GeometryTypes</span><span class='hljl-t'>

 </span><span class='hljl-n'>large_sphere</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Sphere</span><span class='hljl-p'>(</span><span class='hljl-nf'>Point3f0</span><span class='hljl-p'>(</span><span class='hljl-ni'>0</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-nfB'>1f0</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-n'>positions</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>decompose</span><span class='hljl-p'>(</span><span class='hljl-n'>Point3f0</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>large_sphere</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-n'>colS</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-nf'>RGBAf0</span><span class='hljl-p'>(</span><span class='hljl-nf'>rand</span><span class='hljl-p'>(),</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(),</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(),</span><span class='hljl-t'> </span><span class='hljl-nfB'>1.0</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-nf'>length</span><span class='hljl-p'>(</span><span class='hljl-n'>positions</span><span class='hljl-p'>)]</span><span class='hljl-t'>
 </span><span class='hljl-n'>sizesS</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-n'>Point3f0</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>.*</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.05f0</span><span class='hljl-t'> </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-nf'>length</span><span class='hljl-p'>(</span><span class='hljl-n'>positions</span><span class='hljl-p'>)]</span><span class='hljl-t'>
 </span><span class='hljl-nf'>meshscatter</span><span class='hljl-p'>(</span><span class='hljl-n'>positions</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>colS</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>markersize</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>sizesS</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery/meshscatter_function/media/image.jpg" alt="">

    </p>
</div>

```