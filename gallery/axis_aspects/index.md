## Axis aspects

```@raw html
<pre class='hljl'>
<span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>MakieLayout</span><span class='hljl-t'>
</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>FileIO</span><span class='hljl-t'>

</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>AbstractPlotting</span><span class='hljl-t'>

</span><span class='hljl-n'>scene</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>layout</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>layoutscene</span><span class='hljl-p'>(</span><span class='hljl-ni'>30</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>resolution</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-ni'>1200</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>900</span><span class='hljl-p'>))</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-nf'>LAxis</span><span class='hljl-p'>(</span><span class='hljl-n'>scene</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>3</span><span class='hljl-p'>]</span><span class='hljl-t'>
</span><span class='hljl-n'>tightlimits!</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>axes</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>layout</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>3</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>

</span><span class='hljl-n'>img</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>rotr90</span><span class='hljl-p'>(</span><span class='hljl-n'>MakieGallery</span><span class='hljl-oB'>.</span><span class='hljl-nf'>loadasset</span><span class='hljl-p'>(</span><span class='hljl-s'>&quot;cow.png&quot;</span><span class='hljl-p'>))</span><span class='hljl-t'>

</span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
    </span><span class='hljl-nf'>image!</span><span class='hljl-p'>(</span><span class='hljl-n'>ax</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>img</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-k'>end</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>title</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;Default&quot;</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>title</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;DataAspect&quot;</span><span class='hljl-t'>
</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>aspect</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>DataAspect</span><span class='hljl-p'>()</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>title</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;AxisAspect(418/348)&quot;</span><span class='hljl-t'>
</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>aspect</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>AxisAspect</span><span class='hljl-p'>(</span><span class='hljl-ni'>418</span><span class='hljl-oB'>/</span><span class='hljl-ni'>348</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>title</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;AxisAspect(1)&quot;</span><span class='hljl-t'>
</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>aspect</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>AxisAspect</span><span class='hljl-p'>(</span><span class='hljl-ni'>1</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>title</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;AxisAspect(2)&quot;</span><span class='hljl-t'>
</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>aspect</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>AxisAspect</span><span class='hljl-p'>(</span><span class='hljl-ni'>2</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>title</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;AxisAspect(0.5)&quot;</span><span class='hljl-t'>
</span><span class='hljl-n'>axes</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>]</span><span class='hljl-oB'>.</span><span class='hljl-n'>aspect</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>AxisAspect</span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.5</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>scene</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//axis_aspects/media/image.png" alt="">

    </p>
</div>

```
