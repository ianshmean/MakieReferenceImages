## Legend

```@raw html
<pre class='hljl'>
<span class='hljl-t'>

</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>AbstractPlotting</span><span class='hljl-t'>

</span><span class='hljl-n'>scene</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Scene</span><span class='hljl-p'>(</span><span class='hljl-n'>resolution</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-ni'>500</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>500</span><span class='hljl-p'>))</span><span class='hljl-t'>
</span><span class='hljl-n'>x</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>map</span><span class='hljl-p'>([</span><span class='hljl-sc'>:dot</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-sc'>:dash</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-sc'>:dashdot</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>4</span><span class='hljl-p'>])</span><span class='hljl-t'> </span><span class='hljl-k'>do</span><span class='hljl-t'> </span><span class='hljl-n'>ls</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>lw</span><span class='hljl-t'>
    </span><span class='hljl-nf'>linesegments!</span><span class='hljl-p'>(</span><span class='hljl-t'>
        </span><span class='hljl-nf'>range</span><span class='hljl-p'>(</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>stop</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>length</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>100</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>100</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>100</span><span class='hljl-p'>),</span><span class='hljl-t'>
        </span><span class='hljl-n'>linestyle</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>ls</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>linewidth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>lw</span><span class='hljl-p'>,</span><span class='hljl-t'>
        </span><span class='hljl-n'>color</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-n'>RGBAf0</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-p'>)[</span><span class='hljl-k'>end</span><span class='hljl-p'>]</span><span class='hljl-t'>
</span><span class='hljl-k'>end</span><span class='hljl-t'>
</span><span class='hljl-n'>x</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-n'>x</span><span class='hljl-oB'>...</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-nf'>range</span><span class='hljl-p'>(</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>stop</span><span class='hljl-oB'>=</span><span class='hljl-ni'>5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>length</span><span class='hljl-oB'>=</span><span class='hljl-ni'>100</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>100</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>100</span><span class='hljl-p'>))[</span><span class='hljl-k'>end</span><span class='hljl-p'>]]</span><span class='hljl-t'>
</span><span class='hljl-nf'>center!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>ls</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>AbstractPlotting</span><span class='hljl-oB'>.</span><span class='hljl-nf'>legend</span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-s'>&quot;attribute </span><span class='hljl-si'>$i</span><span class='hljl-s'>&quot;</span><span class='hljl-t'> </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>4</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-n'>camera</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>campixel!</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>raw</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>true</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>st</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Stepper</span><span class='hljl-p'>(</span><span class='hljl-nf'>vbox</span><span class='hljl-p'>(</span><span class='hljl-n'>scene</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>ls</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;output&quot;</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>ls</span><span class='hljl-p'>[</span><span class='hljl-k'>end</span><span class='hljl-p'>]</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-p'>[</span><span class='hljl-sc'>:strokecolor</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>RGBAf0</span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.8</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.8</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.8</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-nf'>step!</span><span class='hljl-p'>(</span><span class='hljl-n'>st</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-p'>[</span><span class='hljl-sc'>:gap</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>15</span><span class='hljl-t'>
</span><span class='hljl-nf'>step!</span><span class='hljl-p'>(</span><span class='hljl-n'>st</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-p'>[</span><span class='hljl-sc'>:textsize</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>12</span><span class='hljl-t'>
</span><span class='hljl-nf'>step!</span><span class='hljl-p'>(</span><span class='hljl-n'>st</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-p'>[</span><span class='hljl-sc'>:linepattern</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>Point2f0</span><span class='hljl-p'>[(</span><span class='hljl-ni'>0</span><span class='hljl-p'>,</span><span class='hljl-oB'>-</span><span class='hljl-nfB'>0.2</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.2</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.2</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-nfB'>1.0</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-oB'>-</span><span class='hljl-nfB'>0.2</span><span class='hljl-p'>)]</span><span class='hljl-t'>
</span><span class='hljl-nf'>step!</span><span class='hljl-p'>(</span><span class='hljl-n'>st</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-p'>[</span><span class='hljl-sc'>:scatterpattern</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>decompose</span><span class='hljl-p'>(</span><span class='hljl-n'>Point2f0</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>Circle</span><span class='hljl-p'>(</span><span class='hljl-nf'>Point2f0</span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>0</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.3f0</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-ni'>9</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>l</span><span class='hljl-p'>[</span><span class='hljl-sc'>:markersize</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nfB'>2f0</span><span class='hljl-t'>
</span><span class='hljl-nf'>step!</span><span class='hljl-p'>(</span><span class='hljl-n'>st</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-n'>st</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//legend_1/media/legend_1-1.png" alt="">

    </p>
</div>

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//legend_1/media/legend_1-2.png" alt="">

    </p>
</div>

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//legend_1/media/legend_1-3.png" alt="">

    </p>
</div>

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//legend_1/media/legend_1-4.png" alt="">

    </p>
</div>

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//legend_1/media/legend_1-5.png" alt="">

    </p>
</div>

```
