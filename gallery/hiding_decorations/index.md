## Hiding decorations

```@raw html
<pre class='hljl'>
<span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>MakieLayout</span><span class='hljl-t'>

</span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>AbstractPlotting</span><span class='hljl-t'>

</span><span class='hljl-n'>scene</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Scene</span><span class='hljl-p'>(</span><span class='hljl-n'>resolution</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-ni'>600</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>600</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-n'>camera</span><span class='hljl-oB'>=</span><span class='hljl-n'>campixel!</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>layout</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>GridLayout</span><span class='hljl-p'>(</span><span class='hljl-t'>
    </span><span class='hljl-n'>scene</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-cs'># we need to specify rows and columns so the gap sizes don&#39;t get lost</span><span class='hljl-t'>
    </span><span class='hljl-n'>addedcolgaps</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Fixed</span><span class='hljl-p'>(</span><span class='hljl-ni'>0</span><span class='hljl-p'>),</span><span class='hljl-t'>
    </span><span class='hljl-n'>addedrowgaps</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Fixed</span><span class='hljl-p'>(</span><span class='hljl-ni'>0</span><span class='hljl-p'>),</span><span class='hljl-t'>
    </span><span class='hljl-n'>alignmode</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Outside</span><span class='hljl-p'>(</span><span class='hljl-ni'>30</span><span class='hljl-p'>)</span><span class='hljl-t'>
</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span><span class='hljl-n'>axes</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-nf'>LAxis</span><span class='hljl-p'>(</span><span class='hljl-n'>scene</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-p'>]</span><span class='hljl-t'>
</span><span class='hljl-n'>layout</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>

</span><span class='hljl-n'>re</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>record</span><span class='hljl-p'>(</span><span class='hljl-n'>scene</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;output.mp4&quot;</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>framerate</span><span class='hljl-oB'>=</span><span class='hljl-ni'>3</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-k'>do</span><span class='hljl-t'> </span><span class='hljl-n'>io</span><span class='hljl-t'>
    </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>titlevisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>xlabelvisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>ylabelvisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>xticklabelsvisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>yticklabelsvisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>xticksvisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>yticksvisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
    </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>ax</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>axes</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>bottomspinevisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>leftspinevisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>topspinevisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-n'>ax</span><span class='hljl-oB'>.</span><span class='hljl-n'>rightspinevisible</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-kc'>false</span><span class='hljl-t'>
        </span><span class='hljl-nf'>recordframe!</span><span class='hljl-p'>(</span><span class='hljl-n'>io</span><span class='hljl-p'>)</span><span class='hljl-t'>
    </span><span class='hljl-k'>end</span><span class='hljl-t'>
</span><span class='hljl-k'>end</span><span class='hljl-t'>
</span><span class='hljl-k'>return</span><span class='hljl-t'> </span><span class='hljl-n'>re</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <video controls autoplay loop muted>
  <source src="http://juliaplots.org/MakieReferenceImages/gallery//hiding_decorations/media/hiding_decorations.mp4" type="video/mp4">
  Your browser does not support mp4. Please use a modern browser like Chrome or Firefox.
</video>

    </p>
</div>

```
