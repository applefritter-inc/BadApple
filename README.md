# BadApple

## what does this do??
this is code execution in developer mode in recovery mode. this basically is an exploit that has the same capabilities as SH1mmer, except that the TPM is disabled. why? refer to this: <https://source.chromium.org/chromiumos/chromiumos/codesearch/+/main:src/platform/depthcharge/src/vboot/load_kernel.c;drc=081580ab61e5b5d4df9389bfe3f9f8891a950c9a;l=116>

## erm, i have SH1mmer, this is useless 🤓
this exploit is only intended for boards that have been keyrolled. e.g. nissa, dedede.

## does this work for me
if you don't have disk layout v3(boards made after 2021), you cant do this exploit because you have no internet recovery option because disk layout v2 and below has no miniOS

## how to do badapple
1. enter developer mode with ESC+REFRESH+POWER and CTRL+D
2. when you reach the block screen, press ESC+REFRESH+POWER again
3. select Internet Recovery
4. when miniOS loads in, press CTRL+ALT+F3(open the VT3)
5. you now have a shell you can type shit in ykyk

## why does this stupid exploit so ez work
because when you enter developer mode, cros_debug is flipped to 1 in crossystem's logic \
now the devs forgot that the recovery initramfs should always be trusted, whether in developer mode or not \
so they just put code in miniOS where if cros_debug == 1, open a shell in the VT3 \
because of googles oversight, we have a shell in the VT3 whilst enrolled.
<https://source.chromium.org/chromiumos/chromiumos/codesearch/+/main:src/platform2/minios/ramfs/etc/init/debug-tty.conf;drc=a344af8a24700b3395cbaec1ab9b914f5b3d5b85;l=18>
