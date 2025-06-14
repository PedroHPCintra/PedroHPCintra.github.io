$$ S_0 = \int m v \mathrm{d}s $$

Minima ação $\delta S_0 = 0$

$$ \delta S_0 = 0 \Rightarrow \delta \int m v \mathrm{d}s = 0 $$

mas $v = \displaystyle \frac{\mathrm{d} s}{\mathrm{d} t}$, o que significa que $\mathrm{d} s = v \mathrm{d} t$. Logo

$$ \delta \int m v \mathrm{d}s = \delta \int m v^2 \mathrm{d}t $$

novamente, $m v^2 = 2 E_k$, e energia cinética se relaciona com a energia potencial através da energia total $E = E_k + V$. Portanto,

$$ \delta \int m v^2 \mathrm{d}t = \delta \int 2 E_k \mathrm{d} t = \delta \int E_k + E - V \mathrm{d} t $$

separando a integral

$$ \delta \int E_k - V \mathrm{d} t + \delta \int E \mathrm{d} t = 0 $$

se a energia total $E$ do sistema é conservada, isso significa que ela não varia no tempo, e portanto

$$ \delta \int E \mathrm{d} t = \delta \left(E t \right) = \delta E \cdot t + E \cdot \delta t $$

mas acabamos de assumir que a energia total é conservada, portanto $\delta E = 0$, se considerarmos também que o intervalo de tempo é fixo, todas as possíveis trajetórias ocorrem no mesmo intervalo de tempo, assim $\delta t = 0$. Nos resta

$$ \delta \int E_k - V \mathrm{d} t = 0 $$

Ou seja

$$ \delta \int L \mathrm{d}t = 0 $$

e 

$$ S_0 = \int L \mathrm{d} t $$

Agora suponha uma partícula cuja trajetória está sujeita à uma força resultante de intensidade $F$. Suponha $y(t)$ como sendo a trajetória que minimiza $S_0$ e $q(t)$ uma outra trajetória construída a partir de $y(t)$ somada à um pequeno desvio $\eta(t)$.

$$ q(t) = \underbrace{y(t)}_{\text{real}} + \underbrace{\eta(t)}_{\text{desvio}} $$

Se o desvio for pequeno, em primeira ordem, a diferença entre $S_0[q(t)] - S_0[y(t)]$ é nula e portanto $\delta S_0 = 0$. (Outra forma de introduzir isso talvez seja falando que queremos ver justamente o que implica a minimização da ação de portanto $\delta S_0 =0 $).

Vamos calcular a ação para cada caso. Primeiro para $q(t)$:

---

$$ E_k = \frac{mv^2}{2} = \frac{m}{2} \left( \frac{\mathrm{d} q}{\mathrm{d} t} \right)^2 = \frac{m}{2} \left( \frac{\mathrm{d}}{\mathrm{d} t} (y + \eta) \right)^2 \\
= \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 + m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} + \frac{m}{2} \left( \frac{\mathrm{d} \eta}{\mathrm{d} t} \right)^2 \\
\approx \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 + m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} $$

pois $(\mathrm{d} \eta / \mathrm{d} t)^2 = 0$ e

$$ V = V(q) = V(y + \eta) $$

expandindo a energia potencial em Taylor

$$ V(q) = V(y) + \eta V'(y) + \eta^2 V''(q) + \cdots $$

$$ V(q) \approx V(y) + \eta V'(y) $$

A ação para esta trajetória fica

$$ S_0[q(t)] = \int_{t_1}^{t_2} E_k - V \mathrm{d}t \\
S_0[q(t)] =  \int_{t_1}^{t_2} \left[ \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 + m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} - V(y) - \eta V'(y) \right] \mathrm{d}t \\
= \int_{t_1}^{t_2} \left[ \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 - V(y) \right] \mathrm{d}t + \int_{t_1}^{t_2} \left[ m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} - \eta V'(y) \right] \mathrm{d} t $$

---

Agora para a trajetória $y(t)$, teremos

$$ E_k = \frac{mv^2}{2} = \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 $$

e $V = V(y)$. Dessa forma, a ação para $y(t)$ é bem mais simples.

$$ S_0[y(t)] = \int_{t_1}^{t_2} E_k - V \mathrm{d}t \\
S_0[y(t)] = \int_{t_1}^{t_2} \left[ \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 - V(y) \right] \mathrm{d}t $$

Finalmente, podemos então escrever $\delta S_0$

$$ \delta S_0 = \int_{t_1}^{t_2} \left[ \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 - V(y) \right] \mathrm{d}t \\
+ \int_{t_1}^{t_2} \left[ m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} - \eta V'(y) \right] \mathrm{d} t \\
- \int_{t_1}^{t_2} \left[ \frac{m}{2} \left( \frac{\mathrm{d} y}{\mathrm{d} t} \right)^2 - V(y) \right] \mathrm{d}t $$

Note que o primeiro e último termo são iguais e portanto se cancelam

$$ \delta S_0 = \int_{t_1}^{t_2} \left[ m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} - \eta V'(y) \right] \mathrm{d} t $$

Utilizando integração por partes, podemos reescrever essa variação.

$$ \int_{t_1}^{t_2} \left[ m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} \right] \mathrm{d} t = m \frac{\mathrm{d}y}{\mathrm{d}t} \left. \eta \right|_{t_1}^{t_2} - \int_{t_1}^{t_2} m \frac{\mathrm{d}^2 y}{\mathrm{d}t^2} \eta \mathrm{d} t $$

porém $\eta(t_1) = \eta(t_2) = 0$ (a perturbação não muda os pontos iniciais e finais). Logo

$$ \int_{t_1}^{t_2} \left[ m \frac{\mathrm{d}y}{\mathrm{d}t} \frac{\mathrm{d} \eta}{\mathrm{d} t} \right] \mathrm{d} t = - \int_{t_1}^{t_2} m \frac{\mathrm{d}^2 y}{\mathrm{d}t^2} \eta \mathrm{d} t $$

e a minimização da ação é reescrita como

$$ \delta S_0 = \int_{t_1}^{t_2} \left[ -m \frac{\mathrm{d}^2 y}{\mathrm{d}t^2} \eta - \eta V'(y) \right] \mathrm{d} t \\
= \int_{t_1}^{t_2} \left[ \left(-m \frac{\mathrm{d}^2 y}{\mathrm{d}t^2} - V'(y) \right) \eta \right] \mathrm{d} t = 0$$

Como $\eta$ pode assumir qualquer formato, a única forma desta integral ser nula é se

$$ -m \frac{\mathrm{d}^2 y}{\mathrm{d}t^2} - V'(y) = 0 $$

Lembrando que a força $F$ é justamente o negativo do gradiente do potencial (neste caso de uma única dimensão é justamente $-V'(y)$) e que a segunda derivada de $y$ com relação ao tempo é justamente a aceleração, obtemos

$$ -m a + F = 0 \\
F = ma $$

A segunda lei de Newton é consequência do princípio de minima ação!

## Euler-Lagrange

Para obter a equação de Euler-Lagrange, iremos substituir as energias para ficarem em termos da Lagrangiana nas equações anteriores. Novamente, começando para $q(t)$

$$ S_0[q(t)] = \int_{t_1}^{t_2} L \, \mathrm{d}t $$

Já que $L$ depende da energia cinética e potêncial, escrevemos $L$ como sendo dependente da velocidade $v$ e da posição $q$ da trajetória. De forma mais simplificada, colocamos $L = L(q, \dot{q})$. Portanto

$$ S_0[q(t)] = \int_{t_1}^{t_2} L(q, \dot{q}) \, \mathrm{d}t $$

$$ L(q) = L(y + \eta) $$

$$ L(q, \dot{q}) = L(y,\dot{y}) + \dot{\eta} \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} + \cdots \\
L(q, \dot{q}) \approx L(y,\dot{y}) + \dot{\eta} \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} $$

Ou seja

$$ S_0[q(t)] = \int_{t_1}^{t_2} \left[ L(y,\dot{y}) + \dot{\eta} \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} \right] \mathrm{d}t \\
= \int_{t_1}^{t_2} L(y,\dot{y}) \, \mathrm{d}t + \int_{t_1}^{t_2} \left( \dot{\eta} \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} \right) \mathrm{d}t $$

E então

$$ \delta S_0 = \int_{t_1}^{t_2} L(y,\dot{y}) \, \mathrm{d}t + \int_{t_1}^{t_2} \left( \dot{\eta} \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} \right) \mathrm{d}t - \int_{t_1}^{t_2} L(y,\dot{y}) \, \mathrm{d}t \\
\delta S_0 = \int_{t_1}^{t_2} \left( \dot{\eta} \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} \right) \mathrm{d}t = \int_{t_1}^{t_2} \left( -\frac{\mathrm{d}}{\mathrm{d}t}\eta \frac{\partial L}{\partial \dot{y}} + \eta \frac{\partial L}{\partial y} \right) \mathrm{d}t \\
= \int_{t_1}^{t_2} \left[ \left( -\frac{\mathrm{d}}{\mathrm{d}t} \frac{\partial L}{\partial \dot{y}} + \frac{\partial L}{\partial y} \right) \eta \right] \mathrm{d}t = 0$$

Novamente, se $\eta$ pode assumir qualquer valor, a única forma desta integral ser 0 é

$$ \boxed{\frac{\partial L}{\partial y} -\frac{\mathrm{d}}{\mathrm{d}t} \left(\frac{\partial L}{\partial \dot{y}}\right) = 0} $$

### Mecânica

Se nosso sistema é um sistema mecânico conservativo, $L = E_k - V = mv^2/2 - V$, portanto

$$ \frac{\partial L}{\partial y} = -\frac{\partial V}{\partial y} = F $$

$$ \frac{\mathrm{d}}{\mathrm{d}t} \left(\frac{\partial L}{\partial \dot{y}} \right) = \frac{\mathrm{d}}{\mathrm{d}t} mv = ma $$

assumindo que a massa $m$ é constante. Chegamos mais uma vez na segunda lei de Newton, $\boxed{F = ma}$.

### Eletromagnetismo

Para o eletromagnetismo, passamos de uma teoria a respeito de particulas e corpos para uma teoria a respeito de campos. Portanto, a lagrangiana passa a ser representada pela integral da densidade lagrangeana $\mathcal{L}$ no espaço

$$ L = \int \mathcal{L} \mathrm{d}^3x $$

onde $d^3 x = \mathrm{d}x\mathrm{d}y\mathrm{d}z$. A ação pode ser reescrita como

$$ S_0 = \int L \mathrm{d}t = \int \mathcal{L} \mathrm{d}^4x. $$

Portanto a densidade lagrangiana se torna a grandeza mais importante e daqui para frente quando falarmos de lagrangiana, estaremos nos referindo à densidade lagrangiana $\mathcal{L}$. A lagrangiana pode ser escrita em termos do tensor eletromagnético $F_{\mu\nu}$

$$ F_{\mu \nu} =
\begin{pmatrix}
    0 & E_x & E_y & E_z \\
    -E_x & 0 & B_z & -B_y \\
    -E_y & -B_z & 0 & B_x \\
    -E_z & B_y & -B_x & 0
\end{pmatrix} $$

utilizando a assinatura da métrica $(+,-,-,-)$, cujas componentes são os campos elétrico e magnético $F_{0i} = E_i$ e $F_{ij} = -\varepsilon_{ijk} B_k$. Outra possibilidade é escrever o tensor $F_{\mu \nu}$ a partir do quadri-potencial $A_\mu$ do campo eletromagnético.

$$
A_\mu = 
\begin{pmatrix}
\phi \\
A_x \\
A_y \\
A_z
\end{pmatrix}
$$

A derivada de $A_\nu$ com relação ao quadrivetor $x_\mu$, é escrita como

$$
\partial_\mu A_\nu = 
\begin{pmatrix}
    \partial_0 \phi & \partial_0 A_x & \partial_0 A_y & \partial_0 A_z \\
    \partial_1 \phi & \partial_1 A_x & \partial_1 A_y & \partial_1 A_z \\
    \partial_2 \phi & \partial_2 A_x & \partial_2 A_y & \partial_2 A_z \\
    \partial_3 \phi & \partial_3 A_x & \partial_3 A_y & \partial_3 A_z
\end{pmatrix}
$$

onde $\partial_0 = \partial_t$, $\partial_1 = \partial_x$, $\partial_2 = \partial_y$ e $\partial_3 = \partial_z$. A diferença $\partial_\mu A_\nu - \partial_\nu A_\mu$ nos resulta justamente a matrix $4\times4$

$$
\partial_\mu A_\nu - \partial_\nu A_\mu = 
\begin{pmatrix}
    \partial_0 \phi - \partial_0 \phi & \partial_0 A_x - \partial_1 \phi & \partial_0 A_y - \partial_2 \phi & \partial_0 A_z - \partial_3 \phi \\
    \partial_1 \phi - \partial_0 A_x & \partial_1 A_x - \partial_1 A_x & \partial_1 A_y - \partial_2 A_x & \partial_1 A_z - \partial_3 A_x \\
    \partial_2 \phi - \partial_0 A_y & \partial_2 A_x - \partial_1 A_y & \partial_2 A_y - \partial_2 A_y& \partial_2 A_z - \partial_3 A_y\\
    \partial_3 \phi - \partial_0 A_z & \partial_3 A_x - \partial_1 A_z & \partial_3 A_y - \partial_2 A_z & \partial_3 A_z - \partial_3 A_z
\end{pmatrix}
$$

$$
\partial_\mu A_\nu - \partial_\nu A_\mu = 
\begin{pmatrix}
    0 & \partial_0 A_x - \partial_1 \phi & \partial_0 A_y - \partial_2 \phi & \partial_0 A_z - \partial_3 \phi \\
    \partial_1 \phi - \partial_0 A_x & 0 & \partial_1 A_y - \partial_2 A_x & \partial_1 A_z - \partial_3 A_x \\
    \partial_2 \phi - \partial_0 A_y & \partial_2 A_x - \partial_1 A_y & 0 & \partial_2 A_z - \partial_3 A_y\\
    \partial_3 \phi - \partial_0 A_z & \partial_3 A_x - \partial_1 A_z & \partial_3 A_y - \partial_2 A_z & 0
\end{pmatrix}
$$

reconhecendo $E_i = -\partial_i \phi  - \partial_0 A_i$ e $B_i = \varepsilon_{ijk} \partial_j A_k$, esta matriz se torna o tensor eletromagnético $F_{\mu\nu}$, e portanto $F_{\mu\nu} = \partial_\mu A_\nu - \partial_\nu A_\mu$.

A lagrangiana do campo eletromagético, em termos de $\vec{E}$ e $\vec{B}$ é dada na forma

$$ \mathcal{L}_{EM} = \frac{1}{2} \left( \vec{E}^2 - \vec{B}^2 \right) $$

onde $\vec{E}^2 = \vec{E} \cdot \vec{E} = E_x^2 + E_y^2 + E_z^2$. Como vimos, $\vec{E}$ e $\vec{B}$ podem ser escritos em termos de $F_{\mu\nu}$

$$ E_i = F_{0i} \,\,\, \& \,\,\, F_{ij} = -\varepsilon_{ijk} B_k \Rightarrow B_i = \frac{1}{2}\varepsilon_{ijk} F_{jk} $$

Portanto podemos reescrever

$$
\vec{E}^2 = \sum_{i=1}^3 \left(F_{0i}\right)^2 = F_{0i} F^{0i}
$$

$$
\vec{B}^2 = \frac{1}{2}F_{ij}F^{ij}
$$

A lagrangiana eletromagnética fica então

$$
\mathcal{L}_{EM} = \frac{1}{2} \left( F_{0i} F^{0i} + \frac{1}{2}F_{ij}F^{ij} \right) = -\frac{1}{4} F_{\mu \nu} F^{\mu \nu}
$$

Porém, tudo isso é na ausência de uma corrente externa, juntamente com uma corrente externa $J_\mu$, podemos escrever a lagrangiana como

$$
\mathcal{L}_{EM} = -\frac{1}{4}F_{\mu \nu}F^{\mu \nu} + J^{\mu} A_\mu
$$

Abrindo os termos do tensor eletromagnético

$$
\mathcal{L}_{EM} = -\frac{1}{4}\left(\partial_\mu A_\nu - \partial_\nu A_\mu \right) \left(\partial^\mu A^\nu - \partial^\nu A^\mu \right) - J^\mu A_\mu \\
= -\frac{1}{4} \left( \partial_\mu A_\nu \partial^\mu A^\nu - \partial_\mu A_\nu \partial^\nu A^\mu - \partial_\nu A_\mu \partial^\mu A^\nu - \partial_\nu A_\mu \partial^\nu A^\mu \right) - J^\mu A_\mu
$$

os dois termos do meio são iguais, assim com os dois da ponta

$$
\mathcal{L}_{EM} = -\frac{1}{2} \left(\partial_\mu A_\nu \partial^\mu A^\nu - \partial_\nu A_\mu \partial^\mu A^\nu \right) - J^\mu A_\mu
$$

Substituindo esta lagrangiana na equação de Euler-Lagrange

$$
\partial_\mu \left( \frac{\partial \mathcal{L}_{EM}}{\partial (\partial_\mu A_\nu)} \right) - \frac{\partial \mathcal{L}_{EM}}{\partial A_\nu} = 0
$$

$$
\frac{\partial \mathcal{L}_{EM}}{\partial (\partial_\mu A_\nu)} = \partial^\mu A^\nu - \partial^\nu A^\mu
$$

$$
\frac{\partial \mathcal{L}_{EM}}{\partial A_\nu} = J^\nu
$$

então

$$
-\partial_\mu \left( \partial^\mu A^\nu - \partial^\nu A^\mu \right) + J^\nu = 0
$$

$$
\boxed{\partial_\mu F^{\mu \nu} = J^\nu}
$$

que corresponde à forma tensorial das equações de Maxwell.

## A ação na relatividade

Para interpretarmos o que é a ação, vamos antes ver como esta grandeza pode ser escrita ao levarmos em conta a relatividade especial.

Sabemos que a Hamiltoniana e a Lagrangiana são conectadas através de uma transformada de Legendre

$$
H = \vec{p} \cdot \vec{\dot{q}} - L
$$

e portanto

$$
L = \vec{p} \cdot \vec{\dot{q}} - H
$$

mas $H$ representa também a energia do sistema, desde que ele seja conservativo, e no caso de uma partícula livre relativística $E = \gamma m c^2$, sendo $\gamma$ o fator de Lorentz.

$$
\gamma = \frac{1}{\sqrt{1 - \frac{v^2}{c^2}}}
$$

Já o primeiro termo, pode ser reescrito como

$$
\vec{p} \cdot \vec{v} = \gamma m \vec{v} \cdot \vec{v} = \gamma m v^2
$$

Ou seja, a lagrangiana assume a forma

$$
L = \gamma m v^2 - \gamma m c^2 = \gamma m (v^2 - c^2)
$$

$$
L = \frac{m (v^2 - c^2)}{\sqrt{1 - v^2/c^2}}
$$

reescrevendo $(v^2 - c^2)$ como $-c^2(1 - v^2/c^2)$, obtemos

$$
L = -mc^2 \frac{1 - v^2/c^2}{\sqrt{1 - v^2/c^2}} = -mc^2 \sqrt{1 - \frac{v^2}{c^2}}
$$

Voltando agora para a expressão da ação e colocando a lagrangiana dentro da integral

$$
S_0 = -mc^2 \int \sqrt{1 - \frac{v^2}{c^2}} \mathrm{d}t
$$

Mas o termo dentro do integrando é justamente a definição do tempo próprio para uma partícula livre se movendo com velocidade $v$. Portanto, a ação se resume a

$$
S_0 = -mc^2 \int \mathrm{d} \tau
$$

Ou seja, a ação é dada em termos de o tempo experienciado por um observador ao se mover em uma trajetória. A minimização da ação significa então minimizar o tempo próprio dentro de uma linha de mundo, ou seja, minimizar o tempo experienciado por um observador ao se mover no espaço-tempo. No limite clássico, a ação assume a forma padrão expressa pela integral da lagrangiana.

Caso a particula esteja sujeita a um potencial, a lagrangiana é subtraída a energia potencial associada à posição da partícula

$$
L = -mc^2 \sqrt{1 - \frac{v^2}{c^2}} - V(x)
$$

e portanto a ação também apresenta um termo potencial, juntamente com o tempo próprio

$$
S_0 = -mc^2 \int \mathrm{d}\tau - \int V(x) \mathrm{d} t
$$

Note que a segunda integral é feita com relação ao tempo $t$ observado no referêncial inercial fixo, não o tempo próprio $\tau$ da partícula. Isso ocorre pois a energia potêncial depende da posição da partícula em relação ao referêncial. Sendo assim a minimização da ação representa agora mais do que a minimização do tempo próprio da partícula ao se mover no espaço-tempo, mas também a minimização deste tempo, juntamente com a configuração de trajetória que dê a menor energia potencial, quando observada por um referencial $O$ qualquer.