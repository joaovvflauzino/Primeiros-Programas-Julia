# Primeiros-Programas-Julia


## EDO 1 <img src="https://latex.codecogs.com/svg.image?\dot&space;u&space;=&space;u(1-u)" title="\dot u = u(1-u)" />
O senhor citou essa EDO na última reunião enquanto passava pelo livro e disse que eu poderia começar por ela. Anotei e fiz como segue.
```
using DifferentialEquations
f(u,p,t) = u*(1-u)
u0 = 2
tspan = (0.0,50.0)
prob = ODEProblem(f,u0,tspan)
sol = solve(prob)

using Plots
plot(sol, title="Solution to the u̇=u(1-u), with u₀=$u0",
     xaxis="Time (t)",yaxis="u(t)")
savefig("Graphic EDO1.png")
```
Foi gerado o gráfico:

![Gráfico da Solução](https://github.com/joaovvflauzino/Primeiros-Programas-Julia/blob/main/Graphic%20EDO1.png)


## EDO 2 <img src="https://latex.codecogs.com/svg.image?\dot&space;u&space;=&space;sin&space;(u)" title="\dot u = sin (u)" />
Essa é a equação (1) estudada na seção 2.1 do Strogatz.
```
using DifferentialEquations
f(u,p,t) = sin(u)
u0 = π/4
tspan = (0.0,5.0)
prob = ODEProblem(f,u0,tspan)
sol = solve(prob)

using Plots
plot(sol,linewidth=5, title="Solution to the u̇=sin(u), with u₀=π/4",
     xaxis="t",yaxis="u(t)", label="Solução pelo Julia")
plot!(sol.t,linewidth=4,ls=:dash, t->2*atan(exp(t)/(1+√2)), label="Solução analítica")
plot!(t->π,lw=2, ls=:dash, label="π")
savefig("Graphic EDO2.png")

```
Esbocei ela usando Julia. Resolvi ela analiticamente (escrevi U em função de t) e coloquei por cima do gráfico anterior, junto com a assíntota (em que u = π).
![Gráfico da Solução](https://github.com/joaovvflauzino/Primeiros-Programas-Julia/blob/main/Graphic%20EDO2.png)


## EDO 3 <img src="https://latex.codecogs.com/svg.image?\dot&space;u=&space;u^2-1" title="\dot u= u^2-1" />
EDO do exemplo 2.2.1
```
using DifferentialEquations
f(u,p,t) = u^2-1
u0 = 0
tspan = (0.0,5.0)
prob = ODEProblem(f,u0,tspan)
sol = solve(prob)

using Plots
plot(sol,linewidth=5, title="Solution to the u̇=u²-1, with u₀=0",
     xaxis="t",yaxis="u(t)", label="Solução pelo Julia")
savefig("Graphic EDO3.png")
```
![Gráfico da Solução](https://github.com/joaovvflauzino/Primeiros-Programas-Julia/blob/main/Graphic%20EDO3.png)

## EDO 4 <img src="https://latex.codecogs.com/svg.image?\dot&space;u=&space;ru(1-\frac{u}{K})" title="\dot u= ru(1-\frac{u}{K})" />
Equação logística, seção 2.3.
```
using DifferentialEquations
r=1/2
K=500
f(u,p,t) = r*u*(1-(u/K))
u0 = 2
tspan = (0.0,30.0)
prob = ODEProblem(f,u0,tspan)
sol = solve(prob)

using Plots
plot(sol,linewidth=5, title="Solution to the u̇=ru(1-u/k), with u₀=2, K=500, r=1/2",
     xaxis="t",yaxis="u(t)", label="Solução pelo Julia")
savefig("Graphic EDO4.png")
```
![Gráfico da Solução](https://github.com/joaovvflauzino/Primeiros-Programas-Julia/blob/main/Graphic%20EDO4.png)

Para <img src="https://latex.codecogs.com/svg.image?u_0>K" title="u_0>K" />:
![Gráfico da Solução](https://github.com/joaovvflauzino/Primeiros-Programas-Julia/blob/main/Graphic%20EDO5.png)
