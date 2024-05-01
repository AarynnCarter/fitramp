JWST Fit Ramp
-------------

Forked branch of Tim Brandt's "fitramp.py" code, which performs chi2 fitting to ramp data. For more details, see:

https://ui.adsabs.harvard.edu/abs/2023arXiv230908753B/abstract
https://ui.adsabs.harvard.edu/abs/2024arXiv240401326B/abstract

and

https://github.com/t-brandt/fitramp

Sole addition is the "expjumpramp.py" file, which refactors the code into a more formalised JWST Step() class. The other files
are not necessary for the code to run. 

Here is an example execution:
```
if __name__ == '__main__':
  import expjumpramp

  # Define your data
  my_jwst_data = "my_jwst_file.fits" #Could also use a datamodel directly!

  # Call the step
  rate, rateints = expjumpramp.ExperimentalJumpRampStep.call(my_jwst_data, 
                                                 save_results=False,
                                                 nproc=4)

  # Save the outputs
  rateints.save("expjumpramp_rateints.fits, dir_path="/my_save_dir/")
  rate.save("expjumpramp_rate.fits", dir_path="/my_save_dir/")
```

Multiprocessing is included in the code, and can be accessed with the `nproc` parameter. You can also scale the readnoise
multiplicatively using the `noise_scale` parameter
