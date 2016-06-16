# Sass-Prefixer-Mixin
SCSS Prefixer Mixin, no more remembering -webkit, -moz, -o, -ms...

Firstly add _prefixer.scss to your assets/stylesheets folder or where-ever you store your SCSS files.

The prefixer will automatically add in the prefixes for -webkit, -moz, -o and -ms for whichever property you give it. For example,
if you wanted to add te prefixes to font-smoothing you would add a font-smoothing mixin like the one below with the prefixer included.

Just include the @include prefixer("mixin-name", $atr); to which-ever mixin requires a prefixer. Simples.

#####mixins.scss
    // Font smoothing (use: @include fontsmooth) defaults to antialised
    @mixin fontsmooth($type: antialiased) {
	      @include prefixer(font-smoothing, $type);
	      font-smoothing: $type;
    }
#####styles.scss

    body {
     @include fontsmooth;
    }
  
Compiles to:

    body {
      -webkit-font-smoothing: antialiased;
      -moz-font-smoothing: antialiased;
      -ms-font-smoothing: antialiased;
      -o-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      font-smoothing: antialiased;
    }
    
You will notice that this one also has -moz-osx which is added if the prefix detects font-smoothing. Otherwise this is ignored.
