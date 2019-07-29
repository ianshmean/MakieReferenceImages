## surface + contour3d

```@raw html
<pre class='hljl'>
<span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>Makie</span><span class='hljl-t'>

 </span><span class='hljl-n'>vx</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-oB'>-</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-nfB'>0.01</span><span class='hljl-oB'>:</span><span class='hljl-ni'>1</span><span class='hljl-t'>
 </span><span class='hljl-n'>vy</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-oB'>-</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-nfB'>0.01</span><span class='hljl-oB'>:</span><span class='hljl-ni'>1</span><span class='hljl-t'>

 </span><span class='hljl-nf'>f</span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>y</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-nf'>sin</span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-oB'>*</span><span class='hljl-ni'>10</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-t'> </span><span class='hljl-nf'>cos</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-oB'>*</span><span class='hljl-ni'>10</span><span class='hljl-p'>))</span><span class='hljl-t'> </span><span class='hljl-oB'>/</span><span class='hljl-t'> </span><span class='hljl-ni'>4</span><span class='hljl-t'>

 </span><span class='hljl-n'>p1</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>surface</span><span class='hljl-p'>(</span><span class='hljl-n'>vx</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>vy</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>f</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-n'>p2</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>contour3d</span><span class='hljl-p'>(</span><span class='hljl-n'>vx</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>vy</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>y</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>-&gt;</span><span class='hljl-t'> </span><span class='hljl-nf'>f</span><span class='hljl-p'>(</span><span class='hljl-n'>x</span><span class='hljl-p'>,</span><span class='hljl-n'>y</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>levels</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>15</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>linewidth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>)</span><span class='hljl-t'>

 </span><span class='hljl-n'>scene</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>vbox</span><span class='hljl-p'>(</span><span class='hljl-n'>p1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>p2</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-nf'>text!</span><span class='hljl-p'>(</span><span class='hljl-nf'>campixel</span><span class='hljl-p'>(</span><span class='hljl-n'>p1</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;surface&quot;</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>position</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>widths</span><span class='hljl-p'>(</span><span class='hljl-n'>p1</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>.*</span><span class='hljl-t'> </span><span class='hljl-nf'>Vec</span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>align</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-sc'>:center</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-sc'>:top</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>raw</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>true</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-nf'>text!</span><span class='hljl-p'>(</span><span class='hljl-nf'>campixel</span><span class='hljl-p'>(</span><span class='hljl-n'>p2</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;contour3d&quot;</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>position</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>widths</span><span class='hljl-p'>(</span><span class='hljl-n'>p2</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>.*</span><span class='hljl-t'> </span><span class='hljl-nf'>Vec</span><span class='hljl-p'>(</span><span class='hljl-nfB'>0.5</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>align</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-sc'>:center</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-sc'>:top</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>raw</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>true</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-n'>scene</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery/surface___contour3d/media/image.jpg" alt="">

    </p>
</div>

```