## Parallel Prefix Sum

```@raw html
<pre class='hljl'>
<span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>Makie</span><span class='hljl-t'>
 </span><span class='hljl-k'>import</span><span class='hljl-t'> </span><span class='hljl-n'>Base</span><span class='hljl-oB'>:</span><span class='hljl-t'> </span><span class='hljl-n'>getindex</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>setindex!</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>length</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>size</span><span class='hljl-t'>
 </span><span class='hljl-k'>import</span><span class='hljl-t'> </span><span class='hljl-n'>Base</span><span class='hljl-oB'>.+</span><span class='hljl-t'>
 </span><span class='hljl-k'>using</span><span class='hljl-t'> </span><span class='hljl-n'>GeometryTypes</span><span class='hljl-t'>

 </span><span class='hljl-k'>function</span><span class='hljl-t'> </span><span class='hljl-nf'>prefix_sum</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>func</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>l</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>length</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>k</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>ceil</span><span class='hljl-p'>(</span><span class='hljl-n'>Int</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nf'>log2</span><span class='hljl-p'>(</span><span class='hljl-n'>l</span><span class='hljl-p'>))</span><span class='hljl-t'>
     </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-oB'>=</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-n'>k</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-oB'>=</span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-n'>j</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-n'>j</span><span class='hljl-oB'>:</span><span class='hljl-nf'>min</span><span class='hljl-p'>(</span><span class='hljl-n'>l</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-n'>k</span><span class='hljl-p'>)</span><span class='hljl-t'>
         </span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>func</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-oB'>-</span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-p'>(</span><span class='hljl-n'>j</span><span class='hljl-oB'>-</span><span class='hljl-ni'>1</span><span class='hljl-p'>)],</span><span class='hljl-t'> </span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>])</span><span class='hljl-t'>
     </span><span class='hljl-k'>end</span><span class='hljl-t'>
     </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>j</span><span class='hljl-oB'>=</span><span class='hljl-p'>(</span><span class='hljl-n'>k</span><span class='hljl-oB'>-</span><span class='hljl-ni'>1</span><span class='hljl-p'>)</span><span class='hljl-oB'>:-</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>1</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-oB'>=</span><span class='hljl-ni'>3</span><span class='hljl-oB'>*</span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-p'>(</span><span class='hljl-n'>j</span><span class='hljl-oB'>-</span><span class='hljl-ni'>1</span><span class='hljl-p'>)</span><span class='hljl-oB'>:</span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-n'>j</span><span class='hljl-oB'>:</span><span class='hljl-nf'>min</span><span class='hljl-p'>(</span><span class='hljl-n'>l</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-n'>k</span><span class='hljl-p'>)</span><span class='hljl-t'>
         </span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>func</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-oB'>-</span><span class='hljl-ni'>2</span><span class='hljl-oB'>^</span><span class='hljl-p'>(</span><span class='hljl-n'>j</span><span class='hljl-oB'>-</span><span class='hljl-ni'>1</span><span class='hljl-p'>)],</span><span class='hljl-t'> </span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>])</span><span class='hljl-t'>
     </span><span class='hljl-k'>end</span><span class='hljl-t'>
     </span><span class='hljl-n'>y</span><span class='hljl-t'>
 </span><span class='hljl-k'>end</span><span class='hljl-t'>

 </span><span class='hljl-k'>mutable struct</span><span class='hljl-t'> </span><span class='hljl-n'>AccessArray</span><span class='hljl-t'> </span><span class='hljl-oB'>&lt;:</span><span class='hljl-t'> </span><span class='hljl-nf'>AbstractArray</span><span class='hljl-p'>{</span><span class='hljl-n'>Nothing</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>}</span><span class='hljl-t'>
     </span><span class='hljl-n'>length</span><span class='hljl-oB'>::</span><span class='hljl-n'>Int</span><span class='hljl-t'>
     </span><span class='hljl-n'>read</span><span class='hljl-oB'>::</span><span class='hljl-n'>Vector</span><span class='hljl-t'>
     </span><span class='hljl-n'>history</span><span class='hljl-oB'>::</span><span class='hljl-n'>Vector</span><span class='hljl-t'>
 </span><span class='hljl-k'>end</span><span class='hljl-t'>

 </span><span class='hljl-k'>function</span><span class='hljl-t'> </span><span class='hljl-nf'>AccessArray</span><span class='hljl-p'>(</span><span class='hljl-n'>length</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>read</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[],</span><span class='hljl-t'> </span><span class='hljl-n'>history</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[])</span><span class='hljl-t'>
     </span><span class='hljl-nf'>AccessArray</span><span class='hljl-p'>(</span><span class='hljl-n'>length</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>read</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>history</span><span class='hljl-p'>)</span><span class='hljl-t'>
 </span><span class='hljl-k'>end</span><span class='hljl-t'>

 </span><span class='hljl-nf'>length</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>::</span><span class='hljl-n'>AccessArray</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>length</span><span class='hljl-t'>
 </span><span class='hljl-nf'>size</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>::</span><span class='hljl-n'>AccessArray</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>length</span><span class='hljl-p'>,)</span><span class='hljl-t'>

 </span><span class='hljl-k'>function</span><span class='hljl-t'> </span><span class='hljl-nf'>getindex</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>::</span><span class='hljl-n'>AccessArray</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-nf'>push!</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>read</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-k'>return</span><span class='hljl-t'>
 </span><span class='hljl-k'>end</span><span class='hljl-t'>

 </span><span class='hljl-k'>function</span><span class='hljl-t'> </span><span class='hljl-nf'>setindex!</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>::</span><span class='hljl-n'>AccessArray</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-nf'>push!</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>history</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>read</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]))</span><span class='hljl-t'>
     </span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>read</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[]</span><span class='hljl-t'>
 </span><span class='hljl-k'>end</span><span class='hljl-t'>

 </span><span class='hljl-oB'>+</span><span class='hljl-p'>(</span><span class='hljl-n'>a</span><span class='hljl-oB'>::</span><span class='hljl-n'>Nothing</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>b</span><span class='hljl-oB'>::</span><span class='hljl-n'>Nothing</span><span class='hljl-p'>)</span><span class='hljl-oB'>=</span><span class='hljl-n'>a</span><span class='hljl-t'>
 </span><span class='hljl-n'>A</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>prefix_sum</span><span class='hljl-p'>(</span><span class='hljl-nf'>AccessArray</span><span class='hljl-p'>(</span><span class='hljl-ni'>8</span><span class='hljl-p'>),</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-p'>)</span><span class='hljl-t'>

 </span><span class='hljl-k'>function</span><span class='hljl-t'> </span><span class='hljl-nf'>render</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-oB'>::</span><span class='hljl-n'>AccessArray</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>olast</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>depth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>0</span><span class='hljl-t'>
     </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>y</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>history</span><span class='hljl-t'>
         </span><span class='hljl-p'>(</span><span class='hljl-nf'>any</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>.≤</span><span class='hljl-t'> </span><span class='hljl-n'>olast</span><span class='hljl-p'>))</span><span class='hljl-t'> </span><span class='hljl-oB'>&amp;&amp;</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>depth</span><span class='hljl-t'> </span><span class='hljl-oB'>+=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>)</span><span class='hljl-t'>
         </span><span class='hljl-n'>olast</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>maximum</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>])</span><span class='hljl-t'>
     </span><span class='hljl-k'>end</span><span class='hljl-t'>
     </span><span class='hljl-n'>maxdepth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>depth</span><span class='hljl-t'>
     </span><span class='hljl-n'>olast</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>depth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>0</span><span class='hljl-t'>
     </span><span class='hljl-n'>C</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>[]</span><span class='hljl-t'>
     </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>y</span><span class='hljl-t'> </span><span class='hljl-kp'>in</span><span class='hljl-t'> </span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>history</span><span class='hljl-t'>
         </span><span class='hljl-p'>(</span><span class='hljl-nf'>any</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-ni'>1</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>.≤</span><span class='hljl-t'> </span><span class='hljl-n'>olast</span><span class='hljl-p'>))</span><span class='hljl-t'> </span><span class='hljl-oB'>&amp;&amp;</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>depth</span><span class='hljl-t'> </span><span class='hljl-oB'>+=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>)</span><span class='hljl-t'>
         </span><span class='hljl-nf'>push!</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-p'>((</span><span class='hljl-n'>y</span><span class='hljl-oB'>...</span><span class='hljl-p'>,),</span><span class='hljl-t'> </span><span class='hljl-n'>A</span><span class='hljl-oB'>.</span><span class='hljl-n'>length</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>maxdepth</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>depth</span><span class='hljl-p'>))</span><span class='hljl-t'>
         </span><span class='hljl-n'>olast</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>maximum</span><span class='hljl-p'>(</span><span class='hljl-n'>y</span><span class='hljl-p'>[</span><span class='hljl-ni'>2</span><span class='hljl-p'>])</span><span class='hljl-t'>
     </span><span class='hljl-k'>end</span><span class='hljl-t'>
     </span><span class='hljl-n'>msize</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.1</span><span class='hljl-t'>
     </span><span class='hljl-n'>outsize</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.15</span><span class='hljl-t'>
     </span><span class='hljl-n'>x1</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>Point2f0</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>))),</span><span class='hljl-t'> </span><span class='hljl-n'>last</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-n'>outsize</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.05</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>x2</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>Point2f0</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>last</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>))),</span><span class='hljl-t'> </span><span class='hljl-n'>last</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-n'>outsize</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.05</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>x3</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>Point2f0</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>last</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>first</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>))),</span><span class='hljl-t'> </span><span class='hljl-n'>last</span><span class='hljl-oB'>.</span><span class='hljl-p'>(</span><span class='hljl-n'>C</span><span class='hljl-p'>)</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>connections</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>Point2f0</span><span class='hljl-p'>[]</span><span class='hljl-t'>

     </span><span class='hljl-n'>yoff</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Point2f0</span><span class='hljl-p'>(</span><span class='hljl-ni'>0</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>msize</span><span class='hljl-t'> </span><span class='hljl-oB'>/</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>ooff</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Point2f0</span><span class='hljl-p'>(</span><span class='hljl-ni'>0</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>outsize</span><span class='hljl-t'> </span><span class='hljl-oB'>/</span><span class='hljl-t'> </span><span class='hljl-ni'>2</span><span class='hljl-t'> </span><span class='hljl-oB'>+</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.05</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-k'>for</span><span class='hljl-t'> </span><span class='hljl-n'>i</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-nf'>length</span><span class='hljl-p'>(</span><span class='hljl-n'>x3</span><span class='hljl-p'>)</span><span class='hljl-t'>
         </span><span class='hljl-nf'>push!</span><span class='hljl-p'>(</span><span class='hljl-n'>connections</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x3</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>.-</span><span class='hljl-t'> </span><span class='hljl-n'>ooff</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x1</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-n'>yoff</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x3</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>.-</span><span class='hljl-t'> </span><span class='hljl-n'>ooff</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x2</span><span class='hljl-p'>[</span><span class='hljl-n'>i</span><span class='hljl-p'>]</span><span class='hljl-t'> </span><span class='hljl-oB'>.+</span><span class='hljl-t'> </span><span class='hljl-n'>yoff</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-k'>end</span><span class='hljl-t'>
     </span><span class='hljl-n'>node_theme</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>Theme</span><span class='hljl-p'>(</span><span class='hljl-t'>
         </span><span class='hljl-n'>markersize</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>msize</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>strokewidth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>3</span><span class='hljl-p'>,</span><span class='hljl-t'>
         </span><span class='hljl-n'>strokecolor</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:black</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-sc'>:white</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.0</span><span class='hljl-p'>),</span><span class='hljl-t'>
         </span><span class='hljl-n'>axis</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-t'>
             </span><span class='hljl-n'>ticks</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>ranges</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>8</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-ni'>1</span><span class='hljl-oB'>:</span><span class='hljl-ni'>5</span><span class='hljl-p'>),),</span><span class='hljl-t'>
             </span><span class='hljl-n'>names</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>axisnames</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-s'>&quot;Array Index&quot;</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-s'>&quot;Depth&quot;</span><span class='hljl-p'>),),</span><span class='hljl-t'>
             </span><span class='hljl-n'>frame</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-p'>(</span><span class='hljl-n'>axis_position</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:none</span><span class='hljl-p'>,)</span><span class='hljl-t'>
         </span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>s</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nf'>scatter</span><span class='hljl-p'>(</span><span class='hljl-n'>node_theme</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x1</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-n'>node_theme</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>x2</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-n'>x3</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:white</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>markersize</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-nfB'>0.2</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>strokewidth</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-ni'>4</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>strokecolor</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:black</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-nf'>scatter!</span><span class='hljl-p'>(</span><span class='hljl-n'>x3</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:red</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>marker</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>&#39;+&#39;</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>markersize</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-n'>outsize</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-nf'>linesegments!</span><span class='hljl-p'>(</span><span class='hljl-n'>connections</span><span class='hljl-p'>,</span><span class='hljl-t'> </span><span class='hljl-n'>color</span><span class='hljl-t'> </span><span class='hljl-oB'>=</span><span class='hljl-t'> </span><span class='hljl-sc'>:red</span><span class='hljl-p'>)</span><span class='hljl-t'>
     </span><span class='hljl-n'>s</span><span class='hljl-t'>
 </span><span class='hljl-k'>end</span><span class='hljl-t'>
 </span><span class='hljl-nf'>render</span><span class='hljl-p'>(</span><span class='hljl-n'>A</span><span class='hljl-p'>)</span><span class='hljl-t'>

</span>
</pre>

```
```@raw html

<div style="display:inline-block">
    <p style="display:inline-block; text-align: center">
        <img src="http://juliaplots.org/MakieReferenceImages/gallery/parallel_prefix_sum/media/image.jpg" alt="">

    </p>
</div>

```