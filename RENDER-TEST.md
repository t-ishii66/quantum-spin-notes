# Render test (temporary)

Temporary probe for how github.com parses inline `$...$`. Delete after measuring.

CASE-01 C1/X1 bare: word $x$ word

CASE-02 C1/X2 ascii-paren: word ($x$) word

CASE-03 C1/X3 zen-paren: 語（$x$）語

CASE-04 C1/X4 ascii-quote: word "$x$ tail" word

CASE-05 C1/X5 zen-quote: 語「$x$」語

CASE-06 C2/X1 bare: word $\mathbf{n}$ word

CASE-07 C2/X2 ascii-paren: word ($\mathbf{n}$) word

CASE-08 C2/X3 zen-paren: 語（$\mathbf{n}$）語

CASE-09 C2/X4 ascii-quote: word "$\mathbf{n}$ tail" word

CASE-10 C2/X5 zen-quote: 語「$\mathbf{n}$」語

CASE-11 C3/X1 bare: word $f(x)$ word

CASE-12 C3/X2 ascii-paren: word ($f(x)$) word

CASE-13 C3/X3 zen-paren: 語（$f(x)$）語

CASE-14 C3/X4 ascii-quote: word "$f(x)$ tail" word

CASE-15 C3/X5 zen-quote: 語「$f(x)$」語

CASE-16 C4/X1 bare: word $\mathbf{n} = (1, 0, 0)$ word

CASE-17 C4/X2 ascii-paren: word ($\mathbf{n} = (1, 0, 0)$) word

CASE-18 C4/X3 zen-paren: 語（$\mathbf{n} = (1, 0, 0)$）語

CASE-19 C4/X4 ascii-quote: word "$\mathbf{n} = (1, 0, 0)$ tail" word

CASE-20 C4/X5 zen-quote: 語「$\mathbf{n} = (1, 0, 0)$」語

CASE-21 C5/X1 bare: word $\vert {+z}\rangle$ word

CASE-22 C5/X2 ascii-paren: word ($\vert {+z}\rangle$) word

CASE-23 C5/X3 zen-paren: 語（$\vert {+z}\rangle$）語

CASE-24 C5/X4 ascii-quote: word "$\vert {+z}\rangle$ tail" word

CASE-25 C5/X5 zen-quote: 語「$\vert {+z}\rangle$」語

CASE-26 C6/X1 bare: word $\cos^2(\theta/2)$ word

CASE-27 C6/X2 ascii-paren: word ($\cos^2(\theta/2)$) word

CASE-28 C6/X3 zen-paren: 語（$\cos^2(\theta/2)$）語

CASE-29 C6/X4 ascii-quote: word "$\cos^2(\theta/2)$ tail" word

CASE-30 C6/X5 zen-quote: 語「$\cos^2(\theta/2)$」語
