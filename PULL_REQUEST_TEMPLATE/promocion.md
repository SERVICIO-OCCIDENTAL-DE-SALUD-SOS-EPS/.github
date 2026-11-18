<!--
Plantilla de PR de promocion. Se abre agregando ?template=promocion.md a la URL de comparacion, por ejemplo:
https://github.com/SERVICIO-OCCIDENTAL-DE-SALUD-SOS-EPS/<repo>/compare/qa...develop?template=promocion.md

Quien hace que:
- Abre: el desarrollador del repo (team developers), con este cuerpo completo.
- Aprueba: el team approvers. En el PR a master aprueba Cesar (cgarcia1978); esa aprobacion es la que
  lee el gate gate-aprobacion-produccion. El autor no aprueba su propio PR.
- Mergea: en qa y master, capa media o devops; un back-merge a develop, el desarrollador. Siempre con
  merge commit (nunca squash ni rebase).

Guia completa en la wiki (repo docs): 40-desarrollo/como-abrir-un-pr-de-promocion.md y 40-desarrollo/flujo-git.md.
-->

## Tipo de promocion

<!-- Marcar una sola. -->

- [ ] `develop` -> `qa`
- [ ] `release/*` -> `qa`
- [ ] `qa` -> `master`
- [ ] `hotfix/*` -> `master`
- [ ] back-merge (`release/*` -> `develop`, `master` -> `develop` o `qa` -> `develop`)

## Commits que entran

<!--
Salida de git log --first-parent sobre el rango que se promueve, por ejemplo:
  git fetch origin
  git log --first-parent --oneline origin/qa..origin/develop          (develop -> qa)
  git log --first-parent --oneline origin/qa..origin/release/<corte>  (release -> qa)
  git log --first-parent --oneline origin/master..origin/qa           (qa -> master)
  git log --first-parent --oneline origin/develop..origin/master      (back-merge master -> develop)
-->

```
(pegar aqui la salida)
```

## Sha de corte

<!-- sha40 del head que se promueve: el tip de develop, de la release, de qa o del hotfix. -->

- Sha:

## Run de qa en verde

<!--
qa -> master: enlace al run de Pipeline del push a qa sobre el sha de corte, en verde (deploy-qa incluido).
hotfix -> master: enlace al run del job hotfix-image sobre la rama hotfix/*.
No aplica a develop -> qa, release -> qa ni back-merge.
-->

- Run:

## Imagen en Harbor

<!--
qa -> master: la imagen qa-<sha40> del tip de qa; deploy-production la re-taguea como production-<sha40>, sin reconstruir.
hotfix -> master: la imagen qa-<sha40> que publico hotfix-image.
No aplica a develop -> qa, release -> qa ni back-merge.
-->

- Imagen: `sos/<imagen>:qa-<sha40>`

## Revisores pedidos

<!--
qa: 2 aprobaciones. master: 2 aprobaciones, al menos 1 del team approvers. develop (back-merge): 1.
Un push nuevo descarta las aprobaciones: pedir la revision con el head definitivo.
-->

- [ ] Pedida al team `approvers`
- [ ] PR a `master`: pedida a Cesar (`cgarcia1978`)

## Ventana de PROD

<!-- Solo qa -> master y hotfix -> master: fecha y hora acordadas para el despliegue. -->

- Ventana:

## Merge

Un PR a `qa` o `master` no lo mergea el autor: lo mergea capa media o devops, con merge commit, cuando estan
las aprobaciones y los checks requeridos en verde sobre el head. Un PR a `master` abierto por una persona entra
sin `--admin`. Un back-merge a `develop` lo mergea el desarrollador, tambien con merge commit.
