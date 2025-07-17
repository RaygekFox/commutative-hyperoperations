# Commutative Hyperoperations

## Introduction and Motivation
This is my notes on my ongoing research of [commutative hyperoperations](https://en.wikipedia.org/wiki/Hyperoperation#Commutative_hyperoperations). They are described in details below, but the idea is that they are an alternative to traditional sequence of operations, also known as [hyperoperations](https://en.wikipedia.org/wiki/Hyperoperation): addition, multiplication, exponentiation, tetration, ... . I'm trying to use them to explore the idea of [functional square root](https://en.wikipedia.org/wiki/Half-exponential_function) of function $\exp(x)$, and use the latter one to deepen the idea of commutative hyperoperations themself. Potentially this could suggest a more natural generalization of tetration to non-integer heights.

There are no serious pre-reqs for reading this, I try to explain all concepts not known to general public.

I do not present any essentially new ideas, but try to offer a different perspective and give more intuition into these topics.

## Classical Hyperoperations
The three classical operations defined on real numbers are addition, multiplication, and exponentiation. Canonically, each next one is introduced as repeated application  of the previous one:

$$
\begin{align}
a\cdot b &= a+a+...+a\quad b\text{ times}
\\
a^b &= a\cdot a\cdot...\cdot a\quad b\text{ times}
\end{align}
$$

This approach immediately defines multiplication and exponentiation only for natural $b$, but it is not too hard to generalize them for real values of $b$.

Since there is an obvious succession of these operation, one can think of possible ways to generalize operations. Instead of using $+,\times$ for addition and multiplication and superscripts for exponentiation, let's choose a more uniform notation:

$$
\begin{align}
a\times_1b&\text{ - addition}
\\
a\times_2b&\text{ - multiplication}
\\
a\times_3b&\text{ - exponentiation}
\end{align}
$$

We can therefore call them "first operation", "second operation", and so on.

It is not hard to come up with a reasonable definition for $a\times_0b$ : it is simply the successor function:

$$a+1+1+...+1\quad b\text{ times }=a+b = a\times_1b$$

It is a bit strange comparing to operations one to three, because it is independent of $b$ – a unary function. But it is not a problem for us, we can still define it as a binary operation, just independent of one of the numbers.

This way, $a\times_4b$ is defined as repeated exponentiation: 

$$a^{a^{a^{...}}}\quad b\text{ times}$$

An important notice is that powers are traditionally calculated from top to bottom, so $a^{a^a}=a^{(a^a)}\neq ({a^a})^a$.

 This operation is known as **tetration**. 

 We can continue this process indefinitely:

$$
    a^{a^{...^a}} \rightarrow a^{a^{...^a}} \rightarrow ...\quad b\text{ towers}
$$

(each arrow means "the number of $a$'s in left tower is")

This is called **pentation**.

You can read more about [hyperoperations](https://en.wikipedia.org/wiki/Hyperoperation).

There are some difficulties with hyperoperations as they are. For example, $\times_n$ for all $n>2$ are not commutative. Also, it's not clear how to generalize them to real or complex values (both bases $a$ and  heights $b$), especially for $n>4$.

Although, there is an alternative approach to defining hyperoperations entirely.

## Commutative Hyperoperations

Let's define a function 

$$
F_1(a,b)=a+b
$$

and a recursive rule:

$$
     F_{n+1}(a,b)=\exp(F_n(\ln (a), \ln (b)))
$$

Taking natural logarithm of both sides of the equation, swapping them, and reducing $n$ by 1 extends this rule to the opposite direction:

$$
     F_{n-1}(a,b)=\ln(F_{n}(\exp(a), \exp(b)))
$$

For $n=2$ we get: 

$$
    F_2(a,b)=\exp(\ln a + \ln b) = \exp(\ln(a\cdot b)) = a\cdot b
$$

We see that $F_1$ is identical to addition, and $F_2$ is identical to multiplication. Although, $F_3$ is not exponentiation: 

$$
F_3(a,b) = \exp(F_2(\ln a,\ln b)) =  \exp(\ln a\cdot \ln b) \neq a^b\neq b^a
$$


But it is not too far either:

$$
F_3(a,b) = e^{\ln a\cdot \ln b} = a^{\ln b} = b^{\ln a}
$$

And therefore

$$F_3(a,e^b) = a^b$$

and

$$F_3(e^a,b) = b^a$$

This diagram explains the relation between the operations:

<img width="584" height="642" alt="Commutative operations diagram" src="https://github.com/user-attachments/assets/4fd81d77-912b-4f29-a024-36919f7e2b36" />

An important observation is that this diagram is fully commutative and can be extended in both directions up and down, assuming that we can apply $\ln$ function to numbers $a$ and $b$ as many times as we want. This is, of course, not true. In fact, from any real number you can only take logarithm a finite number of times before the output becomes $\leq 0$. We will ignore this problem for a moment and assume that we always pick big enough numbers for any given operation. 

To not write nested exponents and logarithms, let's introduce some convenient notation:

$$
\begin{align}
\exp(\exp(...(x)...)\quad n \text{ times}\quad &:=x^{(+n)}
\\
\ln(\ln(...(x)...)\quad n \text{ times}\quad &:=x^{(-n)}
\\
x&=x^{(0)}
\\
F_n(x,y)&:=x\circ_ny
\end{align}
$$

To not confuse with usual powers we can read $x^{(+n)}$ as "$x$ to $n$-th order", and $\circ_n$ as "operation of n-th order" or simply "n-th operation".
The recursive definition becomes:

$$
    x\circ_{n+1}y = (x^{(-1)}\circ_ny^{(-1)})^{(+1)}
$$

If we write the orders of all the numbers on the left side of the equation:

$$
    (x^{(0)}\circ_{n+1}y^{(0)})^{(0)} = (x^{(-1)}\circ_ny^{(-1)})^{(+1)}
$$

Notice how in the right-hand side, comparing to the left-hand side, all orders inside brackets are reduced by 1, and the order of the whole expression is increased by 1.
We can express $\circ_n$ in the right-hand side through $\circ_{n-1}$ :

$$
        (x^{(-1)}\circ_{n}y^{(-1)})^{(+1)} = ((x^{(-2)}\circ_{n-1}y^{(-2)})^{(+1)})^{(+1)}
$$

$(x^{(+1)})^{(+1)}$ is simply $\exp(\exp(x))$, so it is the same as $x^{(+2)}$. And in general, it is easy to show that 

$$
    (x^{(+m)})^{(+n)} = x^{(m+n)}\quad \forall m,n\in \mathbb{Z}
$$

Combining these results we see that

$$
        (x^{(0)}\circ_{n+1}y^{(0)})^{(0)} = (x^{(-2)}\circ_{n-1}y^{(-2)})^{(+2)}
$$

This equation is demostrated by the diagram above: walking from top-left corner straight to the top-right through $F_{n+1}$ is the same as going down twice, to the right along $F_{n-1}$, and up twice. 
More generally:

$$
    (x\circ_ny)=(x^{(-m)}\circ_{n-m}y^{(-m)})^{(+m)}\quad\forall n,m\in\mathbb{Z}
$$

We can think of applying different operations as symmetrical reducing and increasing(or, vice-versa, increasing and reducing) exponential orders of the arguments together with the operation, and the result of the operation respectively.
This means that any operation $\circ_n$ can be "turned" into usual addition ($\circ_1$) by changing the order of arguments, and symmetrically the order of the output. For example, 

$$
    (5\circ_310) = (5^{(-2)}\circ_110^{(-2)})^{(+2)}=\exp(\exp(\ln\ln5+\ln\ln10))
$$

Since $e^{a+b}=e^{b+a}$, we can always swap the arguments in the right-hand side of the expression above. Therefore, all operations $\circ_n$ are commutative. This should not be a surprise given the name "commutative hyperoperations".

One more nice property is any $\circ_{n+1}$ is distributive over $\circ_n$. Let's prove this by induction. We know that multiplication is distributive over addition, this is the base case. Next, assume $\circ_n$ is distributive over $\circ_{n-1}$ and consider the expression

$$
    A=(a\circ_nb)\circ_{n+1}c
$$

Let's reduce the order of n+1-th operation and its arguments by one:

$$
    A=((a\circ_nb)^{(-1)}\circ_{n}c^{(-1)})^{(+1)}
$$

Now let's reduce the order of the first n-th operation:

$$
    A=((a^{(-1)}\circ_{n-1}b^{(-1)})\circ_{n}c^{(-1)})^{(+1)}
$$

Notice how the order of the left bracket itself increased, so is now 0. Now we can distribute $\circ_{n}$ over $\circ_{n-1}$:

$$
    A=((a^{(-1)}\circ_{n}c^{(-1)})\circ_{n-1}(b^{(-1)}\circ_{n}c^{(-1)}))^{(+1)}
$$

Now we will remove all orders -1 by increasing the order inside both arguments of $\circ_{n-1}$:

$$
    A=((a\circ_{n+1}c)^{(-1)}\circ_{n-1}(b\circ_{n+1}c)^{(-1)})^{(+1)}
$$

And now we can finally increase the order inside big brackets(arguments of $\circ_{n-1}$):

$$
    A=((a\circ_{n+1}c)\circ_{n}(b\circ_{n+1}c))\quad _\square
$$

### Recap
1. Main definitions and notation:

$$
\begin{align}
\exp(\exp(...(x)...)\quad n \text{ times}\quad &:=x^{(+n)}
\\
\ln(\ln(...(x)...)\quad n \text{ times}\quad &:=x^{(-n)}
\\
x&=x^{(0)}
\\
(x^{(+m)})^{(+n)} &:= x^{(+m+n)}
\\
x\circ_1y &:= x+y
\\
x\circ_{n+1}y &:= (x^{(-1)}\circ_ny^{(-1)})^{(+1)}
\end{align}
$$

2. All operations $\circ_n$ are commutative and distributive over $\circ_{n-1}$.

3. Rule for change of operations:

$$
    (x\circ_ny)=(x^{(-m)}\circ_{n-m}y^{(-m)})^{(+m)}\quad\forall n,m\in\mathbb{Z}
$$

## Order Arithmetics

Consider an interval $[0,1)$. It's image under $\exp$ operation is $[1,e)$. Image of that interval is $[e,e^e)$. Notice how applying $\exp$ to the original interval divides all non-negative reals into a set of non-overlaping intervals. Furthermore, the image of $[0,1)$ under $\ln$ is $(-\infty, 0)$. It's easy to see that any real number $x$ belongs to exactly one of these intervals. Furthermore, since for any pair of intervals $[a,e^a)$ and $[e^a, e^{e^a})$ the function $\exp$ is 1-to-1, any number $x$ can be uniquely expressed as

$$
x=a^{(+n)},\quad a\in[0,1),n\in\mathbb{Z}\geq -1
$$

Let's call such number $a$ **exponential base** of $x$, and $n$ – **base order** of $x$.

Also let's define two respective functions:

$$
\begin{align}
\beta(x)=a &\iff x=a^{(+n)},\quad a\in[0,1),n\in\mathbb{Z}\geq -1
\\
\omega(x)=n &\iff x=a^{(+n)},\quad a\in[0,1),n\in\mathbb{Z}\geq -1
\end{align}
$$

Here $\beta$ and $\omega$ stand for "base" and "order" respectively. Graph of $\beta(x)$:

<img width="1241" height="427" alt="Screenshot 2025-07-17 at 16 27 36" src="https://github.com/user-attachments/assets/e4989ab2-acbc-45ab-bf05-aaba70efedfe" />

Since $1^{(+4)}=e^{e^{e^e}}=e^{3814279.10476...}\approx10^{1656520}$, most "reasonable" numbers will have base order between -1 and 4.

Notice this property:

$$
x^{(-\omega(x))}=\beta(x)
$$

In other words, we have a function $f(x)=x^{(-\omega(x))}$ that maps reals to interval $[0,1)$. This will be useful for the next topic.
