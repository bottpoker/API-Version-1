# Raising on BottPoker with the API
The API will attempt to correct any situations where the wrong endpoint is engaged, those currently extend to:

- Sending a bet when you are intending a `raise` or `reraise`

The API will **always** provide the required bet, and required minimum raise to a user for reference. When a user is creating their bots, they can rely on the endpoint to guide them on the acceptable `raise_minimum` and `raise_maximum`.

The definitions applied to the `RAISING-GUIDELINES` are based on the following quotes:

> i) raise __must__ be at least the size of the largest previous bet or raise of the current betting round.
> 
> ii) If a player raises 50% or more of the previous bet but less than the `minimum_raise`, that user must make a full `raise`. The `raise` will be exactly the `minimum_raise` allowed.
>
> iii) In `nolimit` and `potlimit`, an `allin` wager of less than a full `raise` does not reopen the betting to a player who has already acted and is not facing at least a full `raise` when the action returns to the user. 
>
> iv) In `potlimit`, at least 50% of a full `raise` is ## Minimum `bet`
 to reopen betting for players who have already acted.
>

## Minimum `bet`
The following rules apply to the `bet_minimum`:

- The minimum bet is the `big_blind`
- In the event the user doesn't have enough `chips` to cover a `big_blind` they will go `allin` on `bet` 

## Minimum `raise`
The following rules apply to the `minimum_raise`:

- The minimum `raise` is the `amount` of the previous `bet` or `raise` called.

## Minimum `reraise`
The following rule(s) apply to the `minimum_reraise`:

- The `minimum_raise` must be at least as much as the previous bet or `raise` in the same round
- The `maximum_reraise` is the size of you stack in `nolimit`.

## Calling a raise without enough chips
The following rules apply to calling a raise when shortstack:

- You can `call` a `raise` with less than the `amount` by going `allin`
    - The remaining chips will be returned to player which raised if no one else is was to `call` or `reraise`.
    - There are more rules around returning chips at `showdown` which are not discussed here.
