# Arsenal Engine

An engine for modelling card games (Magic, Dominion, etc).

## Document language

    <player id="player_1" class="self">
        <zone class="deck">
            <card class="creature" sub_type="goblin" color="red" name="Goblins" power=2 tough=2 cmc=4 uri="mtg://gc/2">
                <resource type="mana" color="red" value="2" />
                <resource type="mana" color="multicolor" value="2" />
                <ability>...</ability>
                The actual text on the card goes here
            </card>
            ...
        </zone>
        <zone class="library">
        </zone>
        <zone class="hand">
            <card class="creature" super_type="legendary" sub_type="dragon" color="red white multicolor" name="Dragon" power=6 tough=6 cmc=6 uri="mtg://gc/4">
                <resource type="mana" color="red" value="1" />
                <resource type="mana" color="white" value="1" />
                <resource type="mana" color="multicolor" value="4" />
                <ability>...</ability>
                ...
            </card>
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

## Node selection language

    selector ::= selector_expr | selector_expr, selector
    selector_expr ::= test | test, op, selector_expr
    test ::= test_atom | test_atom, test
    test_atom ::= ( type_test | attribute_test | class_test | predicate_test )+
    type_test ::= <node type>
        e.g. player, zone, card
    attribute_test ::= "@" <attribute_name> [ "(" <value> ")" ]
        e.g. card@type("creature")
    class_test ::== "." <class_name>
        e.g. zone.hand, completely equivalent to @class("hand").
        Not sure if should have this shorthand for @class(), maybe @type() would make more sense in a card game context?
            i.e. card.creature is card@type("creature")
    predicate_test ::= "[" predicate_expression "]"
        e.g. [@tough>=0]

`attribute_test` can check for the existence of an attribute if no value is given.
If a value is given, it performs the equivalent of `[@attr=value]` if value is a number,
or `[@attr~~value]` if value is a string (thereby treating it as a list).


### Predicate expression

Operators:

    =   attribute value equals <value>, also <, <=, >, >=, !=
    ~=  attribute value as a list contains an element with value <value>, or wholly contains <value> as a list
    ~~  attribute value as a list contains at least some element contained by <value> as a list
    =~  attribute value as a list is wholly contained among the elements of <value> as a list
    (mnemonic: the operand on the ~ side of the operator should be the larger one)
    (maybe replace this with `>` and `<`?)


## Document modification language


## Run-time engine


## Examples


### SBAs

#### Move creatures with <= 0 toughness to their controllers' graveyards

    $('zone.field card@type("creature")[tough<=0]').move($('player:owns(:this) zone.grave'))
    $('.field [type~="creature"][tough<=0]').move($(':this::owner .grave'))

#### Planeswalker uniqueness rule

    $('.field @type("planeswalker")').each(                                         // for each planeswalker on the field
        $('.field @type("planeswalker")[@subtype~~(:this@subtype)]:n-match(n+2)')   // select all planeswalkers on the field that share a subtype with it, as long as there are 2 or more of them
            .move($(':this::owner .grave'))                                         // ... and move them to their owners' graveyards
    )

