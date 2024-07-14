import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt

# Definición de la ecuación diferencial de segundo orden
def homogenous_ode(t, y):
    a = 1  # Coeficiente de y''
    b = 2  # Coeficiente de y'
    c = 1  # Coeficiente de y
    dydt = [y[1], -b*y[1] - c*y[0]]
    return dydt

# Condiciones iniciales
y0 = [1, 0]  # y(0) = 1, y'(0) = 0

# Intervalo de tiempo
t_span = [0, 10]

# Resolver la ecuación diferencial
sol = solve_ivp(homogenous_ode, t_span, y0, t_eval=np.linspace(0, 10, 100))

# Graficar la solución
plt.plot(sol.t, sol.y[0], label='y(t)')
plt.plot(sol.t, sol.y[1], label="y'(t)")
plt.xlabel('t')
plt.ylabel('y')
plt.legend()
plt.title('Solución de la ecuación diferencial homogénea')
plt.show()
