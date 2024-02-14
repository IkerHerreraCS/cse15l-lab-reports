**Failure Inducing Input:**
```
@Test
  public void testReversed() {
    int[] input1 = {1,2,3};
    assertArrayEquals(new int[]{3,2,1}, ArrayExamples.reversed(input1));
  }
```
**Input that doesn't induce failure:**
```
@Test
  public void testReversed() {
    int[] input1 = {};
    assertArrayEquals(new int[]{}, ArrayExamples.reversed(input1));
  }

}
```
![Image](Non-FailureInducingInput.png)\
![Image](FailureInducingInput.png)\

**Before Fix:**
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
**After Fix:**
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
The fix addresses the issues by switching the array being populated 
 and returning `newArray` instead of `arr`.

 Part 2:\
 -----------------
 Command:
 ```
grep -i the 1475-2875-2-14.txt
```
Output:
```
also used for malaria chemotherapy. Adverse central nervous
        of those receiving therapeutic doses [ 1 2 ] . Higher blood
        levels of mefloquine are reached under therapeutic regimens
        3 4 ] . The relative incidence of adverse effects is,
        therefore, probably dose-related, although the concomitant
        is likely, then, that the adverse neurological events
        To date, no satisfactory biochemical explanation of the
        lines of evidence suggest that the endoplasmic reticulum
        might be a neuronal target of mefloquine. Go and others [ 5
        muscle and neuronal tissue. These observations suggest that
        difficult to interpret since the experiments were not
        we investigated the effects of mefloquine on global
        under conditions of ER stress [ 8 ] . Taken together, these
        observations suggest that mefloquine might perturb the
        function of the ER via a disruption of calcium homeostasis.
        deplete the ER calcium pool either by (i) inhibiting the ER
        calcium pump and thereby preventing the replenishment of
        the ER calcium pool or (ii) triggering ER (ryanodine or
        [ 9 ] . These phenomena can be visualized by fluorescence
        calcium-free media are used so that the effect can be
        membrane channels. If the test agent can be shown to
        antagonize the release of calcium by a known ER agonist, it
        can then be concluded that the ER calcium pool is a target
     ...
```
The command is printing out all the lines with `the` in them./
This could be useful to find when a certain word is mentioned./
Command:
```
grep i- plasma 1475-2875-2-14.txt
```
Output:
```
        distinguished from calcium influx mediated via plasma
        plasma membrane influx channels, therefore its failure to
        Mefloquine accumulates to plasma concentrations of 3.8
        at the time of peak plasma concentrations in a few
        patients, do mefloquine plasma concentrations approach the
        in the brain relative to plasma by as much as 30-fold, with
```
The command is printing out all the lines with `plasma` in them./
This could be useful to find when a certain word is mentioned./
Command:
```
grep -n plasma 1475-2875-2-14.txt
```
Output:
```
51:        distinguished from calcium influx mediated via plasma
385:          plasma membrane influx channels, therefore its failure to
677:        Mefloquine accumulates to plasma concentrations of 3.8
680:        at the time of peak plasma concentrations in a few
681:        patients, do mefloquine plasma concentrations approach the
685:        in the brain relative to plasma by as much as 30-fold, with
```
The command is printing out all the lines with `plasma` in them, along with their line numbers.\
This could be useful for finding out when a certain word is mentioned.\
Command:
```
grep -n disruption 1475-2875-2-14.txt
```
Output:
```
40:        function of the ER via a disruption of calcium homeostasis.
86:        mechanism. The disruption of calcium homeostasis by
632:        Mefloquine's disruption of ER calcium homeostasis may
665:        time that prolonged disruptions in Ca 2+homeostasis can
695:        disruption of neuronal calcium homeostasis or ER function
```
The command is printing out all the lines with `disruption` in them, along with their line numbers.\
This could be useful for finding out when a certain word is mentioned.\
Command:
```
grep -v the 1475-2875-2-14.txt
```
Output:
```
        Background
        Mefloquine is a prophylactic antimalarial drug that is
        system (CNS) events have been associated with its use [ 1 2
        ] . Severe CNS events requiring hospitalization occur in
        1:10,000 and 1:200-1200 patients taking mefloquine for
        chemoprophylaxis or treatment, respectively [ 1 2 ] .
        Milder CNS events (e.g. dizziness, headache and insomnia)
        are a more frequent occurrence, being experienced by up to
        25% of patients receiving chemoprophylactic doses and 90%
        (2.1-23 μM) compared with those for prophylaxis (3.8 μM) [
        3 4 ] . The relative incidence of adverse effects is,
        effect of malaria during treatment cannot be dismissed. It
        associated with mefloquine have a biochemical basis.
        neurotoxicity of mefloquine has been proposed. However, two
        6 ] showed that mefloquine affects calcium flux into and
        out of isolated mammalian microsomes obtained from skeletal
        muscle and neuronal tissue. These observations suggest that
        mefloquine might disrupt ER calcium homeostasis, but are
        conducted in an intact cell system. In an unrelated study,
        transcription in rat neuroblastoma (NG108) cells using
        microarrays [ 7 ] . Mefloquine caused a striking
        upregulation of growth arrest and development protein 153
        (GADD153), a transcription factor selectively modulated
        Most ER-active agents (e.g. thapsigargin and ryanodine)
        inositol 1,4,5-trisphosphate (IP
        3 ) activated) calcium release channels
        [ 9 ] . These phenomena can be visualized by fluorescence
        microscopy as a transient increase in cytoplasmic calcium
        ...
```
This command prints out all the lines without `the` in them.\
This could be useful for narrowing down the lines you want.\
Command:
```
grep -v to
```
Output:
```
 Background
        Mefloquine is a prophylactic antimalarial drug that is
        also used for malaria chemotherapy. Adverse central nervous
        system (CNS) events have been associated with its use [ 1 2
        ] . Severe CNS events requiring hospitalization occur in
        1:10,000 and 1:200-1200 patients taking mefloquine for
        chemoprophylaxis or treatment, respectively [ 1 2 ] .
        Milder CNS events (e.g. dizziness, headache and insomnia)
        25% of patients receiving chemoprophylactic doses and 90%
        of those receiving therapeutic doses [ 1 2 ] . Higher blood
        levels of mefloquine are reached under therapeutic regimens
        (2.1-23 μM) compared with those for prophylaxis (3.8 μM) [
        3 4 ] . The relative incidence of adverse effects is,
        therefore, probably dose-related, although the concomitant
        effect of malaria during treatment cannot be dismissed. It
        is likely, then, that the adverse neurological events
        associated with mefloquine have a biochemical basis.
        lines of evidence suggest that the endoplasmic reticulum
        might be a neuronal target of mefloquine. Go and others [ 5
        out of isolated mammalian microsomes obtained from skeletal
        muscle and neuronal tissue. These observations suggest that
        mefloquine might disrupt ER calcium homeostasis, but are
        conducted in an intact cell system. In an unrelated study,
        we investigated the effects of mefloquine on global
        microarrays [ 7 ] . Mefloquine caused a striking
        upregulation of growth arrest and development protein 153
        observations suggest that mefloquine might perturb the
        function of the ER via a disruption of calcium homeostasis.
        Most ER-active agents (e.g. thapsigargin and ryanodine)
        deplete the ER calcium pool either by (i) inhibiting the ER
        calcium pump and thereby preventing the replenishment of
        the ER calcium pool or (ii) triggering ER (ryanodine or
        3 ) activated) calcium release channels
        ...
```
This command prints out all the lines without `to` in them.\
This could be useful for narrowing down the lines you want.\
Command:
```
grep -C 2 plasma 1475-2875-2-14.txt
```
Output:
```
concentrations (for example see [ 10 ] ). Nominally
        calcium-free media are used so that the effect can be
        distinguished from calcium influx mediated via plasma
        membrane channels. If the test agent can be shown to
        antagonize the release of calcium by a known ER agonist, it
--
          calcium pump, suggests that mefloquine mobilizes ER
          calcium stores. Glutamate induces the activation of
          plasma membrane influx channels, therefore its failure to
          illicit a calcium response shows that the external media
          contained low levels of free calcium. Therefore the
--
        might be responsible for reported disturbances in emotion [
        22 ] .
        Mefloquine accumulates to plasma concentrations of 3.8
        and 2.1-23 μM after administration at prophylactic dose and
        therapeutic dosing respectively [ 3 4 ] . Therefore, only
        at the time of peak plasma concentrations in a few
        patients, do mefloquine plasma concentrations approach the
        threshold necessary (> 10 μM) to induce any of the
        effects observed in the present study. However, in human
        post-mortem cases, mefloquine has been found to accumulate
        in the brain relative to plasma by as much as 30-fold, with
        absolute, equivalent concentrations exceeding 50 μM (Table
        3). These observations have been confirmed in rats, where
```
This command prints out the number of lines stated after `C-` that are before and after the argument.\
This could be useful for getting context around a keyword.\
Command:
```
grep -C 1 influx 1475-2875-2-14.txt
```
Output:
```
calcium-free media are used so that the effect can be
        distinguished from calcium influx mediated via plasma
        membrane channels. If the test agent can be shown to
--
          calcium stores. Glutamate induces the activation of
          plasma membrane influx channels, therefore its failure to
          illicit a calcium response shows that the external media
--
          elevation of intracellular calcium cannot be attributed
          to influx from an external source. The subsequent ability
          of the neurons to elicit a response after restoration of
--
          attributable to the effect of mefloquine on the ER
          calcium store, and the subsequent sustained influx of
          external calcium (Figure 4). We next investigated the
--
        on the ER Ca 2+-ATPase results in a decrease in the rate of
        calcium influx across the ER membrane. As a consequence of
        a passive leak of calcium ions across the ER membrane into
```
This command prints out the number of lines stated after `C-` that are before and after the argument.\
This could be useful for getting context around a keyword.\

All command line options found at: `https://docs.rackspace.com/docs/use-the-linux-grep-command`









