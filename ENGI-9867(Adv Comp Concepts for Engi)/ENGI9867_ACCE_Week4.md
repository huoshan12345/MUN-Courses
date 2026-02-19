# NFA & DFA

#### Kleene Theorem  

For every NFA an equivalent DFA can be constructed.

For the NFA M = ($Σ,S,s_0,Δ,F$) our aim is to...

- In (q,u,q') ∈ Δ there shouldn’t be any u = λ and |u| > 1
- A transition should be present for all symbols in all states
- There shouldn’t be more than one transitions for each configuration.

## NFA/DFA equivalency-Phase 1

Interim steps are populated to eliminate the |u| > 1 in (q,u,q') of Δ.

This expansion transforms Δ into Δ' by replacing triples of (q,u,q') with triples like $(q,σ_1,p_1),(p_1,σ_2,p_2),...,(p_{k-1},σ_k,q')$. A new machine is formed M' = $(Σ,S',s_0,Δ',F')$
