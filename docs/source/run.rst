Run
---

First, create the initial conditions for the 1D simulation: 

Create initial conditions
~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: sh

    cd sim_folder/run
    python3 generate_initial_conditions.py

This will create the file with the initial conditions ``example_1d_initial_conditions.h5``. Then run the simulation with the 1D inputs.

Running in 1D
~~~~~~~~~~~~~

If you compiled the 1D executable (using ``DIM=1``), you can run the simulation using the 1D inputs file.
For a standard or serial execution:

.. code-block:: sh

    ../build/Castro1d.gnu.gamma_law.ex inputs.1d.cyl

Running in 2D
~~~~~~~~~~~~~

If you compiled the 2D executable (using ``DIM=2``), you can run the simulation using the 1D inputs file.
For a standard or serial execution:

.. code-block:: sh

    ../build/Castro2d.gnu.gamma_law.ex inputs.2d.cyl

Three-body recombination
~~~~~~~~~~~~~~~~~~~~~~~~

Three-body recombination is enabled by default. To disable it, add the following
runtime parameter to the simulation inputs file:

.. code-block:: text

    problem.use_three_body_recombination = 0

Set ``problem.use_three_body_recombination = 1`` to enable it again. When disabled,
the three-body contribution in ``problem_source.H`` is set to zero without
evaluating its rate, equivalent to manually setting ``Real three_body = 0``.
Electron-impact ionization and excitation-ionization remain enabled, and the
species and energy sources use the same net rate coefficient.

This option applies to both single-temperature and two-temperature models in all
supported dimensions. Recompile once after adding this option to the source code;
subsequent changes to the input parameter do not require recompilation.
