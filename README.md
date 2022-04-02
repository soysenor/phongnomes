
# Traveling Phongnomes

## The Game
This silly NFT-based phonon transfer game offers network participants a fun
way to learn how to use the Phonon network.

Game participants learn how to identify network terminals, secure connections
between cards, and transfer phonons. Some participants may practice redeeming
phonons - but as you'll learn that comes with a price ...


## The Story

```
Help gnomes travel the world while building your reputation as a gnome guide, or
don't, and gain notoriety.
```

Each gnome is a beautiful NFT bound to a specific phonon on the Phonon network.
In a perfect world, these phonons are transferred an infinite number of times
between network participants - in effect sending these gnomes on an endless
voyage around the globe.

```
'Tis time! We gnomes must depart our safe oaken tree homes to travel the world.  
Winds of the seas. Snow-packed mountains. Parched lips in desert sun. Things
we've heard, we want to experience ourselves. How many sites will we see?
For how long will our voyage last? Only time will tell ...
```

But we don't live in a perfect world.  Not all network participants may act in
good faith.  Some may selfishly redeem the phonon and take the gnome NFT for
themselves. Redeeming destroys the phonon, and ends the gnomes voyage.  Very
sad.

```
They were last seen entering the caves. Rumors are they were eaten alive ...
```

Fear not! By broadcasting a gnomes last known location, network participants
can signal their good will and earn reputation as a trustworthy gnome guide.
Redeem and steal a gnome away, and risk never being transferred a gnome again!

## Game Mechanics

### Winning, Kidnapping and Reputation
The goal of the game is to get the gnome from the starting player to the
finishing player after transferring the gnome to *at least* the number of unique
players designated in each round

A player could redeem the phonon at any time - kidnapping the gnome for
themselves and keeping the gnome from reaching its destination.  But, they
would run the risk of never receiving subsequent gnomes after suffering risk to
their reputation.

### Gameplay:
  1. Players may `register` their phonon-card id to the game endpoint for a
     chance to be selected as the `starting player` or `finishing player`;
     Players only interested in transferring the gnome between locations
     do *not need* to register
  2. Game creates phonon
  3. Game mints and transfers new gnome NFT to `derived Ethereum address`
  4. Game registers its phonon's public key with the geolocation interface;
     the public key for the phonon - `gnomePublicKey` - is used to verify if a
     broadcasting player possesses the gnome
  5. Game selects two players at random and designates one as the
     `starting player` and one as the `finishing player`; Game pins two
     random geolocations on map, annotating one as starting position and one
     as ending position
  6. Game transfers phonon to `starting player`
  7. Game starts countdown timer for round
  8. Players coordinate transfer of phonon to each other: `receiving players`
  9. `Receiving players` *may* choose to broadcast proof they possess the phonon
     by signing an attestation across the `gnomePublicKey` and pinning a random
     geolocation on map; line connects previous geolocation to current to
     depict gnome's travels
  10. Round ends when `finishing player` broadcasts proof of gnome possession
      *after* required number of unique players have attested ownership, or
      when countdown expires

### Upon Receipt of Transferred Phonon:
Recipient chooses between:
  - `Broadcasting` geolocation of gnome and/or
  - `Transferring` phonon to another requesting network participant
  - `Redeeming` NFT
  - Does nothing with the phonon

### Broadcasting:
  1. Receiving Player connects to game endpoint and geolocation interface
  2. Receiving Player posts proof of phonon possession by posting attestation
  3. Game checks that player has not previously geolocated gnome; if true,
     increments unique player count, and accepts attestation; Receiving Player
     drops a pin anywhere on global map of the world; line connects previous
     geolocation to current to depict gnome's travels

### Reputation and Score:
  - Reputation is earned by broadcasting; a function of the number of posted
    geolocations that follow each broadcast: the **longer** the array the more
    reputation earned; Boosted for **diversity** of flow; bringing new network
    participants into the gnome flow is healthy but it comes with risks. A TBD
    multiple will boost reputation when subsequent broadcasts come from new
    participants and exhibit new travel chains; in other words, the gnome flows
    through new branches and networks of participants
  - Score is based on the number of chains a user has helped complete. Could
    play around with some  interesting game theory by enticing users to break
    the chain to increase their score but at the same time damage their
    reputation.

### Notoriety:
  - Inverse of reputation; a function of the number of posted geolocations that
    follow each broadcast: the **shorter** the array the more notoriety earned
  - The last known broadcaster is assumed to be notorious

## Interfaces Needed
  1. Geolocation and Registration:
      - How does the creator register the phonon?
      - How is the geolocation entered and where is it logged?
      - How are all geolocations for all gnomes displayed?
      - What data structures are stored when logging activity; hashes of
        cardIds and phonon public keys?
  2. Listings:
      - Which cards want to participate?
      - To whom should we send gnome phonons?
      - How is reputation displayed?
      - How is notoriety displayed?
  4. Gnomes:
      - Contract and interface for creating gnomes
      - Where can people see the gnomes that have been minted?
      - How is the map connected to the Gnomes?

## Ideas / Adders

 - Maybe after every x number of broadcasts, the "ideal resting place" (some
   random geographic location generated when the gnome is registered) a "hot" or
   "cold" listing is generated.  When the geolocation is FINALLY achieved, the
   gnome may be redeemed WITHOUT negative reputation? Or something else could
   happen??

## The Rules
 1. No gnome may embark on a second voyage; only the public key from its first
    encumbrance will be used.
 2. No geolocation may be repeated
 3. No card may broadcast more than one geolocation per gnome; multiple
    broadcasts will be ignored, even if a card receives the same phonon
    more than once.
