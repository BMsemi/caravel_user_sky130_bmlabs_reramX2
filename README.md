
<table>
  <tr>
    <td align="center"><img src="bm-lab-logo-white.jpg" alt="BM LABS Logo" width="200"/></td>
    <td align="center"><img src="chip_foundry_logo.png" alt="Chipfoundry Logo" width="200"/></td>
  </tr>
</table>

# Caravel User SKY130 BM Labs ReRAM Example

This repository contains the Caravel project integration for the BM Labs 32 x 32
ReRAM macro. The reusable IP is maintained independently in the
[`sky130_bmlabs_reram`](https://github.com/Baavanes/sky130_bmlabs_reram)
repository and pinned here as a Git submodule.

The checked-in implementation and signoff artifacts record the previous
hardening run. Re-run `make user_project_wrapper` and review signoff whenever
the IP submodule commit is advanced.

## Get Started Quickly

### Follow these steps to set up your environment and harden the project:

1. **Clone the Repository:**

```
git clone --recurse-submodules https://github.com/Baavanes/caravel_user_sky130_bmlabs_reram.git
```
2. **Prepare Your Environment:**

```
cd caravel_user_sky130_bmlabs_reram
make setup
```
3. **Initialize or update the IP submodule:**

```
git submodule update --init --recursive
```
4. **Harden the User Project Wrapper using LibreLane/OpenLane 2:**

```
make user_project_wrapper
```

5. **If wider analog routing is required, follow the NDR instructions:**

   See `Widen_Analog_Routig_using_NDR.txt`.

The project pins a specific IP commit. Update the IP independently and then
advance the submodule pointer in a separate project commit:

```sh
git -C ip/sky130_bmlabs_reram fetch
git -C ip/sky130_bmlabs_reram checkout <tested-ip-commit>
git add ip/sky130_bmlabs_reram
```
