# 2025 COMP1056 Coursework 01

**Submission Deadline:** 05/11/2025 15:00

**WARNING**: You must used the supplied skeleton `.hdl` files  to implement your solution. Using a different file, or changing the names risks your coursework failing to be marked by the pipeline.


## Inside the ALU: Part 01

### Description

In both this coursework and the next, which is **worth 10% of the final mark for COMP1056**, you are going to implement some of the logic gates which could be used to build part of a CPU, specifically the Arithmetic and Logic Unit (ALU). In this coursework, you will start to design some of the components that will be used inside the ALU, and then in the next coursework, you'll finish creating the constituent parts and then assembling them to form an ALU based on the design of that in a simple 8-bit CPU, such as the 6502.

### Submission and Assessment

You will need to fork this repository and then clone it to your Linux system. Submission is then done via a `git commit` and a `git push` as you have done previously done for other courseworks set in the first year. If you click on the **Build** option on the left-hand side of your GitLab interface, you’ll be able to see the marks and feedback for your submission.

You will be given a mark out of ten for this exercise, which will be shown along with the feedback in the pipeline. 

The final submission made before the deadline will be taken as your mark for this exercise. Please check that the submission system has correctly received and assigned a mark for your submission  (i.e. that your last submission has a mark displayed alongside it) or you may obtain a mark of zero.

It is not possible to remove a submission. Attempting to do so by deleting the pipeline entry or the commit from the gitlab interface will not remove the mark. If you wish a previous submission to be counted, then you will need to **resubmit** that version of the code.

### Coursework 01 Description: Beginning the ALU

In this coursework, there are eight *combinatorial* logic gates that you need to implement. For the first set of gates, the implementation is broadly similar to the gates that form part of **nand2tetris**, projects one and two, so you might also want to look there for inspiration. The following table lists the five gates your are to create:

| Gate | Description |
|------|-------------|
|`Not8`| This has one input bus, `in`, and one output bus, `out`. Each bit of the output should be the inverse (i.e. not) of the corresponding input bit.|
| `And8` | This has two input buses, `a` and `b`, and one output bus, `out`. Each bit of the output should be the result of *and*ing together the corresponding input bits in `a` and `b`.|
| `Or8` |  This has two input buses, `a` and `b`, and one output bus, `out`. Each bit of the output should be the result of *or*ing together the corresponding input bits in `a` and `b`.|
| `Xor8` |  This has two input buses, `a` and `b`, and one output bus, `out`. Each bit of the output should be the result of *exclusive-or*ing together the corresponding input bits in `a` and `b`.|
| `Mux8` | This has two input buses, `a` and `b` and one output bus, `out`. Also present is a `sel` input, which is used to select whether input `a` or `b` is passed to `out`. If `sel` is false, input `a` should be selected, otherwise input `b` should be selected.|
 

Once you have created the first five gates, you can move on to the final three gates and for these you may choose to use some of the gates you have already implemented as part of your solution. The final three gates to create are:

| Gate | Description |
|------|-------------|
|`ZeroOrIn`|This has one input bus, `in`, and one output bus, `out`. It also has an input, `z` which is used to say whether the output (`out`) matches the input (`in`) when `z` is 0, or whether the output is forced to have all bits set to zero (when `z` is 1).|
|`NegateOrIn`|This has one input bus, `in`, and one output bus, `out`. It also has an input, `z` which is used to say whether the output (`out`) matches the input (`in`) when `z` is 0, or whether the output is logical inversion of `in` (i.e. all bits of the bus have been inverted, or *not*-ed) when `z` is 1.|
|`Shift8`|This has one input bus, `in`, and one output bus, `out`. This chip shifts each bit of the input precisely one position along to the right. So bit 1 of `in` becomes bit 0 of `out`, bit 2 of `in` becomes bit 1 of `out` etc. until finally bit 7 of in becomes bit 6 of `out`. Bit 7 of `out` is always set to zero (i.e. false).|

For the final `Shift8` gate, the `.hdl` Hardware Description Language does not provide a mechanism to directly connect an input of your `CHIP` to the output of your `CHIP` without passing through another gate, nor can you directly set an output to be true or false. Therefore, you'll need to consider what logic you could use to connect the inputs to the output so that the value does not change.

**Note** As well as connecting the inputs and outputs of a gate to other gates (or the input and output of the `CHIP` you are designing, when defining and using a gate as a **part** of your implementation you can also specify that an input has a specific value by using the keywords `false` and `true`, outputs can also be omitted if you do not wish to connect them to anything)


### Predefined Gates

Several logic gates are provided for you as part of the **nand2tetris** package (for things like, `And`, `Or` and `Not` etc.)  and it is expected that you will make use of them. All gates described in the **nand2tetris** book have pre-defined versions available.

### Assessment criteria

The pipeline will mark each of your implementation by running the test scripts provided against each gate in turn. If the test script passes, then you will be awarded a mark for that gate. The test scripts are provided as part of this repository so you can test your solution as you develop it by running your solution against the test script in the Hardware Simulator.

For the first five gates (`Not8`, `And8`, `Or8`, `Xor8` and `Mux8`) you will be awarded four marks if they all pass the test script successfully, otherwise you'll be awarded mark between zero and four depending on how many of them work.

For the final three gates (`ZeroOrIn`, `NegateOrIn`, and `Shift8`) each gate will be awarded a mark of two if it passes the test script, otherwise it will be awarded zero.

This leads to total of 10 marks being available.
