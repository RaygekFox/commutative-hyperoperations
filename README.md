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

 This operation is known as **tetration**. It's usually denoted as $a\uparrow\uparrow b$.

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

A detailed exploration of operation $\circ_0$ cna be found in [this paper](https://arxiv.org/pdf/math/0112050) by Michael L. Carrol, where he calls it "join operation".

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

### Exponential Base and Exponential Order

Consider an interval $(0,1]$. It's image under $\exp$ operation is $(1,e]$. Image of that interval is $(e,e^e]$. Notice how applying $\exp$ to the original interval divides all non-negative reals into a set of non-overlaping intervals. Furthermore, the image of $(0,1]$ under $\ln$ is $(-\infty, 0]$. It's easy to see that any real number $x$ belongs to exactly one of these intervals.

Furthermore, since for any pair of intervals $(a,e^a]$ and $(e^a, e^{e^a}]$ the function $\exp$ is 1-to-1, any number $x$ can be uniquely expressed as

$$
x=a^{(+n)},\quad a\in(0,1],n\in\mathbb{Z}\geq -1
$$

Let's call such number $a$ **exponential base** of $x$, and $n$ – **exponential order** of $x$.

Also let's define two respective functions:

$$
\begin{align}
\beta(x)=a &\iff x=a^{(+n)},\quad a\in(0,1],n\in\mathbb{Z}\geq -1
\\
\omega(x)=n &\iff x=a^{(+n)},\quad a\in(0,1],n\in\mathbb{Z}\geq -1
\end{align}
$$

Here $\beta$ and $\omega$ stand for "base" and "order" respectively. Graph of $\beta(x)$:

<img width="1241" height="427" alt="Screenshot 2025-07-17 at 16 27 36" src="https://github.com/user-attachments/assets/e4989ab2-acbc-45ab-bf05-aaba70efedfe" />

Since $1^{(+4)}=e^{e^{e^e}}=e^{3814279.10476...}\approx10^{1656520}$, most "reasonable" numbers will have exponential order between -1 and 4.

Notice this property:

$$
x^{(-\omega(x))}=\beta(x)
$$

In other words, we have a function $f(x)=x^{(-\omega(x))}$ that maps reals to interval $(0,1]$. This will be useful for the next topic.

Since any $x\in (0,1]$ will have exponential order equal to 0, let's call that interval the $0$-th **exponential order interval**. The interval $(1,e]$ will be the first exponential order interval, and so on. $(-\infty, 0]$ is the minus first exponential order interval. In general, notice that $n$-th interval will be $(e^{...e}, e^{e^{...e}}]$ with $n$ $e$'s in the left tower, and $n+1$ in the right, so recalling the standard notation of tetration, it is the same as $[e\uparrow\uparrow n, e\uparrow\uparrow (n+1))$, with respective remark regarding the $(-\infty,0]$.

This way, any number $x$ belongs to $\omega(x)$-th exponential order interval.



### Bounds of exponential order

Let's say we want to do an operation $x\circ_ny$. It is the same as taking the sum $(x^{(-n)}+y^{(-n)})^{(+n)}$. Without the loss of generality, let's assume $x\geq y$. Since $\exp$ function is strictly increasing, this means that 

a) $x^{(-n)}\geq y^{(-n)}$.

b) $x\circ_ny$ is greater than both $x$ and $y$ if and only if both $x^{(-n)}$ and $y^{(-n)}$ are greater than 0. Let's consider the case when they are.

$x^{(-n)}$ belongs to $\omega(x^{(-n)})$-th exponential order interval.

Notice that length of every exponential order interval starting from the second one is greater than the sum of lengths of the previous(non-negative) intervals:

$$
\begin{align}
|(1,e\| &> |(0,1]|
\\
|(e,e^e]| &> |(0,e]| 
\\
...
\end{align}
$$

This means that any number $a$ is smaller than the distance from $a$ to the end of the its next exponential order interval, the $(\omega(a)+1)$-th. Since $y^{(-n)}\leq x^{(-n)}$, their sum cannot reach there too, it can be at most in $(\omega(x)+1)$-th exponential order interval.

So, the exponential order of the sum of two numbers is at most one greater than that of the bigger of the numbers:

$$
\omega(a+b)\leq(\text{max}(\omega(a),\omega(b))+1)
$$

It's easy to see that $\omega(x^{(+n)})=\omega(x)+n$, so in our case:

$$
\begin{align}
\omega(x^{(-n)}+y^{(-n)}) &\leq (\text{max}(\omega(x^{(-n)}),\omega(y^{(-n)}))+1)
\\
\omega(x\circ_ny) &\leq (\text{max}(\omega(x),\omega(y))+1)
\end{align}
$$

This concludes the proof of

> #### Theorem 1
> 
> exponential order of the result of any operation $\circ_n$ is higher than the exponential order of the greater of its arguments by at most 1.

Since we can express $a^b$ as $a\circ_3 e^b$, it follows from this theorem that

> #### Corollary 1.1
> 
> $$
> a^b < \exp(\exp(\text{max}(a,e^b)))
> $$

And since tetration operation can increase the exponential order of its arguments by any number, it means that

> #### Corollary 1.2
>
> Any operation $\circ_n$ grows slower than tetration.


## Half-exponential functions

[Half-exponential function](https://en.wikipedia.org/wiki/Half-exponential_function) or functional square root of $\exp$ is such function $f(x)$ that $f(f(x))=\exp(x)$.

Such functions do exist, with somewhat canonical solution being the Kneser's function, proposed in 1950. It's defined for complex numbers and uses a stable point $Q$ such that $e^Q=Q$. I'm mostly interested in applying hyperoperations to real numbers, so we will try to find a purely real function.

It has been proven, that such a function cannot have a closed-form solution using standard arithmetic operations. Luckily, the concept of exponential base and order will be enough to overcome this.

There are(infintely many) non-closed-form solutions, but as commonly presented, they are not smooth(infinitely-differentiable).

### Continuous non-smooth half-exponential function

I will explain a classical construction of a family of half-exponential function, but using exponential base and order ideas. This will help us avoid cases and iteration in our definition(iteration is "hidden" in calculation of $\beta(x)$ and $\omega(x)$ ).

Let's choose a number $x$ and calculate its exponental base and order: 

$$x=\beta(x)^{(\omega(x))}$$

Now consider a function that maps $x$ to the sum of these numebrs:

$$IN(x) = \omega(x)+\beta(x)$$

IN stands for **interval normalization function**.

Here is a very nice thing about it: since $\omega(x)$ is an integer and $\beta(x) \in (0,1]$, they essentially represent a real number as its integer and fractional part. They almost give the standard decimal notation for $IN(x)$ with a small exception for when $\beta(x)=1$, then it gives the next integer after $\omega(x)$. This way, image of each exponential order interval has length 1.

Therefore, if we take $x$ and $e^x$, their images will be 1 apart:

$$IN(x)+1 = IN(e^x)$$

Furthermore, $IN$ is 1-to-1 from $\mathbb{R}$ to $\mathbb{R}_{>-1}$, so $IN^{-1}$ exists(simply raise the fractional part of a number to the order of its whole part).

This way, $\exp(x)$ is identical to taking $IN$ of $x$, adding 1, and applying $IN^{-1}$ to the result:

$$\exp(x) = IN^{-1}(IN(x)+1)$$

And it lets us naturally define a half-exponential function:

$$\exp^{\frac12}(x) = IN^{-1}(IN(x)+\frac12)$$

Of course, no need to stop on half-exponential funciton – we can easily define any fractional iteration of it:

$$\exp^{a}(x) = IN^{-1}(IN(x)+a)\quad \forall a \in [0,1)$$

Don't forget that not all such functions will be defined for all $x$, since $IN^{-1}$ is only defined for $x>-1$.

Such $\exp^{a}$ is identical to the function, defined in [the wikipedia article](https://en.wikipedia.org/wiki/Half-exponential_function), linked above.

If you are happy with function differentiable only twice, you are good to go. We are about to solve this, but the result function won't have all its derviatives positive everythwere(will have kind of bumps), so there is a tradeoff.

To see why this function is only differentiable twice, take a look at $IN^{-1}(x)$ on the interval $(0,2]$:

<img width="620" height="421" alt="Screenshot 2026-01-01 at 17 18 44" src="https://github.com/user-attachments/assets/111e538b-af01-4651-9f8b-b69a04ebc0cc" />

The first half(black) is identical to $f(x)=x$, since we are raising a number to the 0-th order. The right half(red) is identical to $f(x)=e^{x-1}$. At the point where they meet, only their values and first derivatives are equal.

### Smooth half-exponential function

The workaround to get a smooth function would be to find such a function $f(x)$ that:

$$
\begin{align}
&f(0)=0
\\
&f(1)=1
\\
&\frac{\text{d}^n f}{\text{d}x^n}(1) = \frac{\text{d}^n e^{f(x-1)}}{\text{d}x^n}(1) \quad \forall n\in N
\end{align}
$$

This is tricky, but one way to do this is to "morph" $x$ into $e^{x-1}$ using smooth bump function flat on both ends. That it a function changing from one value to another on some interval with all its derivatives equal to 0 on the ends of the interval.

For this, we need some non-constant funciton that has all derivatives (approaching) 0 at some point. One such function is $f(x)=e^{-/frac{1}{x}}$. It's only defined for $x>0$, but that's good enough. Then we do the following:

<img width="853" height="168" alt="Screenshot 2026-01-01 at 18 24 15" src="https://github.com/user-attachments/assets/1c232d32-d68f-4298-b324-e74934fea64a" />

This function $g$ works as weight to smoothly turn $x$ into $e^{x-1}$:

$$h(x) = x\cdot g(1-x) + e^{1-x}\cdot g(x)$$

So now, combining $h(x)$ for $(0,1]$ and $e^{h(x-1)}$ for $[1,e)$ gives us exactly the function with properties we wanted.

It's important to say that we could choose another function instead of $e^{-/frac{1}{x}}$ – any function defined on $(0,1]$ and all derivatives approaching 0 will do. So the choice we made is not natural in any sense, and we are actually talking about a family of half-exponential functions and a specific example of one.

That weighted function $h$ is a modification of $IN^{-1}$, so its inverse $h^{-1}$ is a modification of $IN$. So we can call $h^{-1}$ a **smooth interval normalization function** and denote it $IN_h(x)$.

If needed for clarity, we could denote the original non-smooth one $IN_x$, implying identity function $f(x)=x$.

So, the smooth fractional exponential function is:

$$\exp^{a}(x) = IN_h^{-1}(IN_h(x)+a)\quad \forall a \in [0,1)$$

If we want $a$ to be any number outside of $[0,1)$ interval, we round it down, apply exponential(logarithmic if negative) function respective number of times, and then this fractional exponential. 

Here is a plot of $IN_h^{-1}(x)$ for $x\in(0,2]$:

<img width="699" height="351" alt="Screenshot 2026-01-03 at 17 15 17" src="https://github.com/user-attachments/assets/31c835ae-0e8c-4d0f-929c-0f831ae1882b" />

As you see, it has two bumps, on each half. I'm not sure if it's possible to avoid this. The weighted sum approach will most likely not work.
