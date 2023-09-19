`x = gamultiobj(fun,nvars)` 在由 `fun` 定义的目标函数的[帕累托前沿](https://uk.mathworks.com/help/gads/gamultiobj.html#bvg2667)上找到 `x`。`nvars` 是优化问题的维度（决策变量的数量）。解 `x` 是局部的，这意味着它可能不在全局帕累托前沿上。

**Note**

[Passing Extra Parameters](https://uk.mathworks.com/help/optim/ug/passing-extra-parameters.html) explains how to pass extra parameters to the objective function and nonlinear constraint functions, if necessary.

[传递额外参数](https://uk.mathworks.com/help/optim/ug/passing-extra-parameters.html) 解释了如何在必要时将额外参数传递给目标函数和非线性约束函数。



`x = gamultiobj(fun,nvars,A,b)` 在满足线性不等式 *A*∗*x*≤*b* 的条件下找到一个局部帕累托集 `x`。参见[线性不等式约束](https://uk.mathworks.com/help/optim/ug/linear-constraints.html#brhkghv-14)。`gamultiobj` 仅对默认的 `PopulationType` 选项（`'doubleVector'`）支持线性约束。

`x = gamultiobj(fun,nvars,A,b,Aeq,beq)` 在满足线性等式 *A**e**q*∗*x*=*b**e**q* 和线性不等式 *A*∗*x*≤*b* 的条件下找到一个局部帕累托集 `x`，参见[线性等式约束](https://uk.mathworks.com/help/optim/ug/linear-constraints.html#brhkghv-15)。（如果不存在不等式，设置 `A = []` 和 `b = []`。）`gamultiobj` 仅对默认的 `PopulationType` 选项（`'doubleVector'`）支持线性约束。

`x = gamultiobj(fun,nvars,A,b,Aeq,beq,lb,ub)` 定义了设计变量 `x` 的一组下界和上界，以便在范围 `lb ≤ x ≤ ub` 内找到一个局部帕累托集，参见[边界约束](https://uk.mathworks.com/help/optim/ug/bound-constraints.html)。如果不存在线性等式约束，请使用空矩阵作为 `Aeq` 和 `beq`。`gamultiobj` 仅对默认的 `PopulationType` 选项（`'doubleVector'`）支持边界约束。

`x = gamultiobj(fun,nvars,A,b,Aeq,beq,lb,ub,nonlcon)` 根据 `nonlcon` 中定义的约束找到一个帕累托集。函数 `nonlcon` 接受 `x` 并返回向量 `c` 和 `ceq`，分别代表非线性不等式和等式。`gamultiobj` 最小化 `fun`，使得 `c(x) ≤ 0` 和 `ceq(x) = 0`。（如果没有边界，设置 `lb = []` 和 `ub = []`。）`gamultiobj` 仅对默认的 `PopulationType` 选项（`'doubleVector'`）支持非线性约束。

`x = gamultiobj(fun,nvars,A,b,Aeq,beq,lb,ub,options)` 或 `x = gamultiobj(fun,nvars,A,b,Aeq,beq,lb,ub,nonlcon,options)` 使用 `options` 中的值替换默认的优化参数，以找到一个帕累托集 `x`。使用 [`optimoptions`](https://uk.mathworks.com/help/optim/ug/optim.problemdef.optimizationproblem.optimoptions.html)（推荐）或结构体来创建 `options`。

`x = gamultiobj(fun,nvars,A,b,Aeq,beq,lb,ub,nonlcon,intcon)` 或 `x = gamultiobj(fun,nvars,A,b,Aeq,beq,lb,ub,nonlcon,intcon,options)` 要求列在 `intcon` 中的变量取整数值。



**Note**

当存在整数约束时，`gamultiobj` 不接受非线性等式约束，仅接受非线性不等式约束。

`x = gamultiobj(problem)` 为 `problem` 找到帕累托集，其中 `problem` 是在 [`problem`](https://uk.mathworks.com/help/gads/gamultiobj.html#bvf79ug_sep_bvf79ug-problem) 中描述的结构体。

`[x,fval] = gamultiobj(___)`，对于任何输入变量，都会返回一个矩阵 `fval`，它代表了在 `fun` 中定义的所有适应度函数在 `x` 中所有解的值。`fval` 有 `nf` 列，其中 `nf` 是目标的数量，并且与 `x` 的行数相同。

`[x,fval,exitflag,output] = gamultiobj(___)` 返回 `exitflag`，一个标识算法停止原因的整数，以及 `output`，一个包含有关优化过程信息的结构体。

`[x,fval,exitflag,output,population,scores] = gamultiobj(___)` returns `population`, whose rows are the final population, and `scores`, the scores of the final population.

`[x,fval,exitflag,output,population,scores] = gamultiobj(___)` 返回 `population`，其行是最终种群，以及 `scores`，即最终种群的得分。

## 
