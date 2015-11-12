# perl6-Lingua-EN-Conjugate

##### A Perl6 module that conjugates English verbs

### Usage

     use Lingua::EN::Conjugate;

     my $verb = englishverb.new(bare => 'code', forms => <BeIng HaveEn>);
     for < I you he she it we you they > -> $s {
       for < p sp > -> $t {
         $verb.tense = $t;
         say $verb.conjugate( subject => $s );
       }
     }

### Methods details

Method **conjugate** returns Array: accepts named parameters :
- subject       : String any of <I he she it we you they>
- bare          : String required, Bare form of the verb without the "to"
- mod           : String, any of <will shall may can>
- tense         : String, any of <p sp> ; "p" = Present, "sp" = Past 
- forms         : Array of String, many of = <BeIng BeEn HaveEn>;   BeIng = continuous,  BeEn = Passive, HaveEn = Perfect
- negation      : Bool default False;
- shortneg      : Bool default False, use the short negation ( ex: [will not] => [won't] );
- interrogative : Bool default False, Use interrogative form



### Purpose And Notes

> **Warning, this is not a direct port of the Perl5 "Lingua-EN-Conjugate" module !**
>
> Instead of using fixed tense blocks to conjugate an English verb, this module uses notions of "forms" which can be combined.
> IE: The "Past Perfect Continuous/Progressive" of a verb is in this case, The "Perfect" and "Continuous" forms conbined and evaluated with the "Past Tense"
>
> The notions used by the module:
> SUBJECT: 
>> The sentence's actor, any of <I he she it we you they>.
> TENSE: 
>> The grammatical time of the action. "Time" is a physical notion, "Tense" a grammatical one. English has only 2 "Tense": Past and Present; The "Future" tense is a modality.
>> Two Tenses are aviable: p = Present, sp = Past
> MODALITY:
>> Allows speakers to evaluate a proposition relative to a set of other propositions (Necessity or Possibility). The "future" (will) stands for a Possibility.
>> Modality is any of <will shall may can>
> VERB:
>> Conveys an action (bring, read, walk, run, learn), or a state of being (be, exist, stand).
> VERBAL FORM:
>> Way in which a verb is structured in relation to time, BE+ING = Continuity, non-finite. HAVE+EN: Past event linked to the present, BE+EN: Passive verbal form
>> Modality can be many of <>

#### Speculative Todo List

- Subject alias (ex: they/'Alexandra and Mary') 
- Short forms for: "I am" "will" "would" etc ...
- "be able to"
- "used to"
- "ought to"
- "Explain" method for educational purpose
- Multi method with pure grammatical arguments ex: conjugate( tense => "Past Perfect Continuous" )

#### Copyright

Copyright © 2015 Nuguet Romuald under the Artistic License 2.0.

