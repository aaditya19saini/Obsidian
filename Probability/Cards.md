# Cards and poker hands: a probability guide

Card problems are useful for practicing sample spaces, combinations, conditional probability, and the complement rule. Unless a problem says otherwise, assume a standard deck, a uniformly shuffled deck, and no jokers.

## A quick guide to playing cards

If you do not play cards often, these basics are enough to follow the probability examples:

- A **card** has a rank and a suit. For example, the **7 of hearts** has rank 7 and suit hearts.
- The four **suits** are clubs (♣), diamonds (♦), hearts (♥), and spades (♠). Each suit has 13 cards. Diamonds and hearts are red; clubs and spades are black.
- The **ranks** are 2, 3, 4, 5, 6, 7, 8, 9, 10, jack (J), queen (Q), king (K), and ace (A). Jack, queen, and king are often called **face cards**. In many poker straights, an ace can be high (10-J-Q-K-A) or low (A-2-3-4-5), but it cannot wrap around (Q-K-A-2-3 is not a straight).
- A **hand** is the group of cards dealt to one player. In the examples here, it means five cards. The order of cards in a hand does not matter: holding 2♣, 5♦, 7♥, 9♠, K♣ is the same hand whichever order they were dealt.
- A **rank match** means cards have the same number or letter, regardless of suit. For example, 8♣ and 8♥ are a pair of eights.

### Common five-card hand names

These names describe patterns in the ranks and suits of a five-card hand:

- **Pair:** two cards share a rank, such as two queens. “One pair” means the other three cards have different ranks from the pair and each other.
- **Two pair:** two cards of one rank and two of another, such as two 4s and two kings, plus one extra card.
- **Three of a kind:** three cards share a rank, such as three 8s, plus two other cards.
- **Straight:** five consecutive ranks, such as 4-5-6-7-8. The suits can differ.
- **Flush:** all five cards have the same suit. Their ranks do not need to be consecutive.
- **Full house:** three cards of one rank and two of another, such as three 8s and two kings.
- **Four of a kind:** four cards share a rank, such as four aces, plus one extra card.
- **Straight flush:** a straight where all five cards also share the same suit.
- **High card:** none of the patterns above; the hand is described by its highest card.

In ordinary poker, these categories are ordered roughly from most common to rarest as high card, one pair, two pair, three of a kind, straight, flush, full house, four of a kind, straight flush. “Royal flush” is the special name for the ace-high straight flush (10-J-Q-K-A of one suit).

## The standard deck

A standard deck has 52 distinct cards: 4 suits (clubs, diamonds, hearts, and spades), with 13 ranks in each suit (2 through 10, jack, queen, king, ace).

- There are 13 cards of each rank and 4 cards of each suit.
- There are ==26 red cards and 26 black cards==.
- A five-card hand is an unordered selection: the order in which the cards are dealt does not matter.

When drawing without replacement, draws are dependent. For example, after drawing an ace, 3 aces remain among 51 cards. This is why a binomial model generally does not describe a fixed number of draws from a deck without replacement.

## Counting hands

The number of ways to choose $k$ objects from $n$, when order does not matter, is the binomial coefficient:

$$
\binom{n}{k}=\frac{n!}{k!(n-k)!}
$$

Thus the number of five-card hands is:

$$
|\Omega|=\binom{52}{5}=2,598,960
$$

If all five-card hands are equally likely, then for any event $A$:

$$
P(A)=\frac{\text{number of hands in }A}{\binom{52}{5}}
$$

This is an example of the classical probability rule: count favorable outcomes and divide by the number of equally likely outcomes.

### When order matters

If cards are dealt into ordered positions, use permutations instead. The number of ordered sequences of $k$ distinct cards from a deck of $n$ is:

$$
(n)_k=n(n-1)\cdots(n-k+1)=\frac{n!}{(n-k)!}
$$

For example, the number of ordered ways to deal five cards is $52\cdot51\cdot50\cdot49\cdot48$. Each unordered hand corresponds to $5!$ orders, so dividing by $5!$ gives $\binom{52}{5}$.

## The five-card poker hands

Poker hand names classify five-card hands. The table gives the number and probability of each category in a standard five-card draw. Here a straight flush includes a royal flush; a royal flush is the ace-high straight flush.

| Hand category | Count | Probability (approximately) | How it is counted |
|---|---:|---:|---|
| Straight flush | 40 | 0.001539% | 10 possible consecutive rank sequences per suit, times 4 suits |
| Four of a kind | 624 | 0.02401% | Choose the rank (13), then the fifth card (48) |
| Full house | 3,744 | 0.1441% | Choose triple rank, its 3 suits, pair rank, and its 2 suits |
| Flush (not straight flush) | 5,108 | 0.1965% | Choose 5 of 13 ranks in a suit, excluding its 10 straight sequences; times 4 |
| Straight (not straight flush) | 10,200 | 0.3925% | 10 rank sequences, any suits ($4^5$), excluding 4 same-suit outcomes per sequence |
| Three of a kind | 54,912 | 2.1128% | Choose triple rank and suits, then two distinct side ranks and suits |
| Two pair | 123,552 | 4.7539% | Choose 2 ranks for pairs and their suits, then a different side card |
| One pair | 1,098,240 | 42.2569% | Choose pair rank and suits, then 3 distinct side ranks and suits |
| High card (no pair, straight, or flush) | 1,302,540 | 50.1177% | Remaining hands |

The category counts sum to $\binom{52}{5}$, so the categories partition the sample space. Their probabilities therefore sum to 1 (up to rounding).

### Full house (Blitzstein and Hwang, Example 1.4.18)

A full house has three cards of one rank and two cards of another rank, such as three 8s and two kings. Count them by making each choice:

1. Choose the rank for the three-of-a-kind: $13$ choices.
2. Choose 3 of the 4 cards of that rank: $\binom{4}{3}$ choices.
3. Choose a different rank for the pair: $12$ choices.
4. Choose 2 of the 4 cards of that rank: $\binom{4}{2}$ choices.

Therefore:

$$
N_{\text{full house}}=13\binom{4}{3}\cdot12\binom{4}{2}=3,744
$$

$$
P(\text{full house})=\frac{3,744}{\binom{52}{5}}\approx0.0014406=0.14406\%
$$

This follows the multiplication-rule tree used in Blitzstein and Hwang's Example 1.4.18. Equivalently, their notation writes the suit choices as $\binom{4}{3}$ and $\binom{4}{2}$. The role of each rank is specified (triple first, pair second), so each full house is counted exactly once. Dividing by the total number of equally likely five-card hands gives:

$$
P(\text{full house})=\frac{13\binom{4}{3}\,12\binom{4}{2}}{\binom{52}{5}}=\frac{3,744}{2,598,960}\approx0.00144
$$

The book emphasizes that the exact answer in binomial-coefficient form shows where the count comes from; the decimal is useful for interpreting how rare the hand is.

## Example: at least one ace

It is often simpler to count the complement. There are $\binom{48}{5}$ hands with no ace, because all five cards must come from the 48 non-aces. Hence:

$$
P(\text{at least one ace})=1-\frac{\binom{48}{5}}{\binom{52}{5}}\approx0.3412
$$

So roughly 34.1% of five-card hands contain at least one ace.

## Example: exactly two hearts

Choose 2 of the 13 hearts and 3 of the 39 non-hearts. The number of such hands is $\binom{13}{2}\binom{39}{3}$, giving:

$$
P(\text{exactly 2 hearts})=\frac{\binom{13}{2}\binom{39}{3}}{\binom{52}{5}}
$$

This is a hypergeometric calculation: sampling without replacement from two groups (hearts and non-hearts).

## Example: two aces in a five-card hand

For exactly two aces, choose 2 of the 4 aces and 3 of the 48 non-aces:

$$
P(\text{exactly 2 aces})=\frac{\binom{4}{2}\binom{48}{3}}{\binom{52}{5}}
$$

More generally, if a population has $K$ successes among $N$ objects, and $n$ objects are sampled without replacement, the probability of exactly $k$ successes is:

$$
P(X=k)=\frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}
$$

This is the hypergeometric distribution. A card draw has this structure because each drawn card changes the composition of the remaining deck. See [[Conditional probability]] and [[Independence]].

## A reliable counting workflow

1. Define the experiment precisely: deck, number of cards, replacement or no replacement, and whether order matters.
2. Define the sample space. For an unordered five-card hand from 52 cards, it has $\binom{52}{5}$ equally likely outcomes.
3. Translate the event into choices by rank and suit. Keep choices distinct when they serve different roles, such as the triple rank and pair rank in a full house.
4. Check for overlap. If categories can overlap, use inclusion-exclusion or split them into disjoint cases. For example, “flush” and “straight” overlap in straight flushes.
5. Divide favorable outcomes by total outcomes, or use the complement when that is easier.
6. Sanity-check that the count is no larger than the sample space and that disjoint category counts add up correctly.

## Related probability ideas

- **Combinations:** unordered selections, such as a five-card hand: $\binom{n}{k}$.
- **Permutations:** ordered selections, such as a specific sequence of cards dealt: $(n)_k$.
- **Complement rule:** $P(A)=1-P(A^c)$, useful for “at least one” events.
- **Conditional probability:** after observing some cards, restrict the sample space to the cards still possible.
- **Hypergeometric distribution:** counts successes in sampling without replacement.
- **Inclusion-exclusion:** corrects for overlap when combining events, such as a straight or a flush.

## Reference

Blitzstein, Joseph K., and Jessica Hwang. *Introduction to Probability*. See Chapter 1, Example 1.2.3 (“Pick a card, any card”) for describing card events as sets, and Example 1.4.18 (“Full house in poker”) for the full-house count and probability. The book’s exercises also ask for flush and two-pair probabilities. The hand-category table above uses conventional mutually exclusive poker categories; poker texts and problems can use different conventions about whether a straight flush is included in a flush, so check the wording of the event.
