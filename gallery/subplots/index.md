## subplots

```@raw html
<pre class='hljl'>
<span class='hljl-t'>

</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>AbstractPlotting</span><span class='hljl-t'>

</span><span class='hljl-n'>scene1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>scene2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>scene3</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>scene4</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Scene</span><span class='hljl-p'>(),</span><span class='hljl-t'> </span><span class='hljl-nf'>Scene</span><span class='hljl-p'>(),</span><span class='hljl-t'> </span><span class='hljl-nf'>Scene</span><span class='hljl-p'>(),</span><span class='hljl-t'> </span><span class='hljl-nf'>Scene</span><span class='hljl-p'>()</span><span class='hljl-t'>

</span><span class='hljl-nf'>lines!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>10</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-oB'>=:</span><span class='hljl-n'>red</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-nf'>lines!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>10</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-oB'>=:</span><span class='hljl-n'>blue</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-nf'>lines!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>10</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-oB'>=:</span><span class='hljl-n'>green</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>10</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-oB'>=:</span><span class='hljl-n'>red</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>10</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-oB'>=:</span><span class='hljl-n'>blue</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>rand</span><span class='hljl-p'>(</span><span class='hljl-ni'>10</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-oB'>=:</span><span class='hljl-n'>orange</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-nf'>barplot!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene3</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>randn</span><span class='hljl-p'>(</span><span class='hljl-ni'>99</span><span class='hljl-p'>))</span><span class='hljl-t'>

</span><span class='hljl-nf'>v</span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-oB'>::</span><span class='hljl-nf'>Point2</span><span class='hljl-p'>{</span><span class='hljl-n'>T</span><span class='hljl-p'>})</span><span class='hljl-t'> </span><span class='hljl-n'>where</span><span class='hljl-t'> </span><span class='hljl-n'>T</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Point2f0</span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>],</span><span class='hljl-t'> </span><span class='hljl-ni'>4</span><span class='hljl-oB'>*</span><span class='hljl-n'>x</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>])</span><span class='hljl-t'>
</span><span class='hljl-nf'>streamplot!</span><span class='hljl-p'>(</span><span class='hljl-n'>scene4</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>v</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-oB'>-</span><span class='hljl-nfB'>2..2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-oB'>-</span><span class='hljl-nfB'>2..2</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-nf'>vbox</span><span class='hljl-p'>(</span><span class='hljl-nf'>hbox</span><span class='hljl-p'>(</span><span class='hljl-n'>scene2</span><span class='hljl-p'>,</span><span class='hljl-n'>scene1</span><span class='hljl-p'>),</span><span class='hljl-nf'>hbox</span><span class='hljl-p'>(</span><span class='hljl-n'>scene4</span><span class='hljl-p'>,</span><span class='hljl-n'>scene3</span><span class='hljl-p'>))</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery//subplots/media/image.png" alt="">

    </p>
</div>

```
