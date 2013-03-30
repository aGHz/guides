= Arsenal Engine

An engine for modelling card games (Magic, Dominion, etc).

== Document language

    <player id="player_1" class="self">
        <zone class="deck">
            <card class="creature goblin red" name="Goblins" power=2 tough=2 mana="2RR" uri="mtg://gc/2">The actual text on the card goes here</card>
            ...
        </zone>
        <zone class="library">
        </zone>
        <zone class="hand">
            <card class="legendary_creature dragon red white multicolor" name="Dragon" power=6 tough=6 mana="4RW" uri="mtg://gc/4">...</card>
            ...
        </zone>
        <zone class="field">
            <zone class="lands"></zone>
            <zone class="attack"></zone>
            <zone class="block"></zone>
        </zone>
        <zone class="grave">
        </zone>
        <zone class="exile">
        </zone>
    </player>
    <zone class="stack">
        <ability ...>
    </zone>

== Node selection language

== Document modification language


== Examples

=== SBAs

Move creatures with <= 0 toughness to their controllers' graveyards

    $('zone.field card[type~="creature"][tough<=0]').move($('player:owns(:this) zone.grave'))
    $('.field [type~="creature"][tough<=0]').move($(':this::owner .grave'))

Planeswalker uniqueness rule

    $('.field [type~="planeswalker"]').each( $('.field [type~="planeswalker"][subtype~~(:this[subtype])]:n-match(n+2)').move($(':this::owner .grave')) )
    Explained:
    $('.field [type~="planeswalker"]').each(                                                // for each planeswalker on the field
        $('.field [type~="planeswalker"][subtype~~(:this[subtype])]:n-match(n+2)')          // select all planeswalkers on the field that share a subtype with it, as long as there are 2 or more of them
            .move($(':this::owner .grave'))                                                 // ... and move them to their owners' graveyards
    )

