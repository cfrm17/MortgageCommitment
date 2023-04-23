# Mortgage Commitment

The mortgage Commitment model is being used to measure the risk of mortgage commitments. The model is actually based on a two-step process, and in the end allows investor to hedge the inherent interest rate risk imbedded in these mortgage commitments.

In the first stage, the actual mortgage commitment pipeline is “mapped” to a simplified portfolio of European swaptions. In the second stage, this simplified portfolio of swaptions is used to determine an appropriate portfolio of swaps to hedge the swaptions.

The full pipeline of mortgage commitments is valued based on certain assumptions, and a simplified portfolio of swaptions is determined that mimics the risk and values
of the pipeline. To determine the cost of hedging the pipeline, investors will delta-hedge this portfolio of swaptions with a portfolio of swaps.

A mortgage commitment can be approximately regarded as an American look-back option that gives the holder the right to effectively enter into a pay fixed leg of an amortizing swap. 

In practice the holder of the commitment does not actually exercise the option optimally with regards to the American feature of the option. To capture the non-optimality of the exercise, they propose to model these commitments as a series of European swaptions, where the expiry dates on the options is determined using historical closing percentages. 

This effectively assumes that the callalbe option to exercise the commitment is optimally exercised, but the time of exercise is based on historical data. For a given initial commitment term, people have looked at historical closing ratios to express a commitment as a linear combination of European swaptions. The historical exercise dates are then bucketed into monthly time intervals (more precisely, 30 day increments) to determine the expected closing ratios. 

Once this matrix is defined, it is possible to determine how many mortgages in the pipeline are expected to close. A further approximation is made regarding the term that these mortgages close at. This is due to the fact that historically not every commitment ends up closing at the term that the initial commitment was provided. 

Based on historical data, most commitments for 5 year terms actually closed at 5 year, while for others terms this wasn’t true. As a simplified assumption, the model assumes that 100% of the five year commitments actually close at five years, while for the others 80% of the mortgages close at the original commitment term while 20% close at the five year term.

If the initial mortgage commitment term is not five years, then this Ft would be split as 0.8Ft for the original term and 0.2Ft for the five year term. The matrix used Cn is a 23 by 23 matrix, and deals with commitments of maximum 690 days.

There were historically not enough commitments with t > 690 days to be able to predict closing ratios. Therefore, any commitments longer than 690 days that are currently in the pipeline are omitted from the calculation, and we were told this comprised a small portion of the current pipeline.

As discussed previously, these rate commitments are given on mortgages of various terms. This includes 6 month convertible, as well as 1,2,3,4,5,7 and 10 year closed. Using the above described methodology, it is then possible to create a 8 (corresponding to the term) by 23 (corresponding to potential closing dates) grid of expected funding. 

The commitments are (arbitrarily) grouped together as follows: first three months, next two months, next three months, next four months, and remaining months. The time to expiry of the option is taken to be the average funding date of the Commitments.

This will be further demonstrated by example in the results section of the vetting report. Finally, the strike price of each swaption is taken to be the weighted average commitment rate for each group, with the weighting corresponding to the notional multiplied by the closing ratios of the commitments.

References:

https://github.com/cfrm17/MortgageCommitment
