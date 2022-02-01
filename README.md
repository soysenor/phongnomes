
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

## The Rules

  1. No gnome may embark on a second voyage; only the public key from its first
     encumbrance will be used.
  2. No geolocation may be repeated
  3. No card may broadcast more than one geolocation per gnome; multiple
     broadcasts will be ignored, even if a card receives the same phonon
     more than once.

## The Mechanics

### Release:
  1. Creator mints new gnome NFT on some cadence (maybe weekly)
  2. Creator wraps gnome NFT in a phonon on the their card
  3. Creator registers the public key for that phonon with geolocation
     interface; this key gnomePublicKey is used to verify if a broadcasting
     network participant possesses the gnome
  4. Creator broadcasts the initial geolocation of the gnome; this is the first
     known location of the gnome
  5. Creator transfers the phonon to a random member of the posted list of
     interested network participants; excluding known or possible bad actors

### Upon Receipt of Transferred Phonon:
Recipient chooses among the following
  - Broadcasts geolocation of gnome and/or
  - Transfers the phonon to another requesting network participant
  - Redeems the NFT
  - Does nothing with the phonon

### Broadcasting:
  1. Network participant connects to geolocation interface
  2. Interface verifies the connected peer possesses a gnome; check card for
     registered gnomePublicKey
  3. Interface verifies the connected peer has not yet geolocated gnome; check
     if key exists hashCardIDGnomeKey
  4. Network participant drops a pin anywhere on global map of the world; log
     geolocation and accreditation

     *best data structures tbd, but conceptually:*

     gnomePublicKey | geolocation | hashCardID | hashCardIDGnomeKey
     ---|---|---|---

### Reputation:
  - Earned by broadcasting; a function of the number of posted geolocations that
    follow each broadcast: the **longer** the array the more reputation earned
  - Boosted for **diversity** of flow; bringing new network participants into
    the gnome flow is healthy but it comes with risks. A TBD multiple will
    boost reputation when subsequent broadcasts come from new participants and
    exhibit new travel chains; in other words, the gnome flows through new
    branches and networks of participants

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
