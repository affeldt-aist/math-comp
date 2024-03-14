# Changelog (unreleased)

To avoid having old PRs put changes into the wrong section of the CHANGELOG,
new entries now go to the present file as discussed
[here](https://github.com/math-comp/math-comp/wiki/Agenda-of-the-April-23rd-2019-meeting-9h30-to-12h30#avoiding-issues-with-changelog).

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

### Added

- in `ssrint.v`
  + lemmas `intrN`, `intrB`

- in `ssrnum.v`
  + lemma `invf_pgt`, `invf_pge`, `invf_ngt`, `invf_nge`
  + lemma `invf_plt`, `invf_ple`, `invf_nlt`, `invf_nle`

- in `path.v`
  + lemma `count_sort`

- in `order.v`
  + structures `meetSemilatticeType`, `bMeetSemilatticeType`,
    `tMeetSemilatticeType`, `tbMeetSemilatticeType`,
	`joinSemilatticeType`, `bJoinSemilatticeType`,
	`tJoinSemilatticeType`, `tbJoinSemilatticeType`,
	`tDistrLatticeType`, `bOrderType`, `tOrderType`, `tbOrderType`,
	`cDistrLatticeType` (relatively complemented distributive lattices),
	`ctDistrLatticeType` (dually sectionally complemented distributive lattices),
	`finBPOrderType`, `finTPOrderType`, `finTBPOrderType`,
	`finMeetSemilatticeType`, `finBMeetSemilatticeType`,
	`finJoinSemilatticeType`, and `finTJoinSemilatticeType`.
  + `rcompl x y z` is the relative complement of `z` in `[x, y]` defined for any
    `cDistrLatticeType` instance.
  + `codiff x y` is the dual sectional complement of `y` in `[x, \top]` defined
    for any `ctDistrLatticeType` instance.

### Changed

- in `bigop.v`
  + weaken hypothesis of lemma `telescope_sumn_in`

- in `zmodp.v`
  + simpler statement of `Fp_Zcast`

- in `path.v`
  + generalized `count_merge` from `eqType` to `Type`

- in `order.v`
  + The dual instances are now definitionally involutive, i.e., canonical
    instances of an order structure on `T^d^d` and `T` are convertible (the
    latter instance may require an eta-expansion on the type record for
    technical reasons). Similarly, canonical instances of an order structure on
    `(T1 *p T2)^d` and `T1^d *p T2^d` are convertible.
  + In order to achieve the above definitional properties on displays, the type
    of display is changed from `unit` to `Order.disp_t`, which is a primitive
    record type consisting of two fields of type `unit`.
  + The default displays for product and lexicographic orders are now defined
    separately for cartesian products and sequences. They take displays of the
    parameter types as parameters.
    * `prod_display d1 d2` is the default display for the product order of
      cartesian products of the form `T1 * T2`, where `T1` and `T2` have
      canonical orders of displays `d1` and `d2`, respectively.
    * `seqprod_display d` is the default display for the product order of
      sequences and tuples.
    * `lexi_display d1 d2` is the default display for the lexicographic order of
      cartesian products.
    * `seqlexi_display d` is the default display for the lexicographic order of
      sequences and tuples.
  + The operator notations for `seqprod_display` and `seqlexi_display` now use
    `^sp` and `^sl` in place of `^p` and `^l`, respectively.
  + `finLatticeType`, `finDistrLatticeType`, `finOrderType`, and
    `finCDistrLatticeType` now do not require the existence of top and bottom
    elements, i.e., their instances are not necessarily inhabited.
    Their counterparts with top and bottom are now `finTBLatticeType`,
	`finTBDistrLatticeType`, `finTBOrderType`, and `finCTBDistrLatticeType`,
    respectively.

### Renamed

- in `order.v` (cf. Changed section)
  + `finLatticeType` -> `finTBLatticeType`
  + `finDistrLatticeType` -> `finTBDistrLatticeType`
  + `finOrderType` -> `finTBOrderType`
  + `finCDistrLatticeType` -> `finCTBDistrLatticeType`

### Removed

- in `div.v`
  + definition `gcdn_rec`, use `gcdn` directly

- in `binomial.v`
  + definition `binomial_rec`, use `binomial` directly

- in `bigop.v`
  + definition `oAC_subdef`, use `oAC` directly

- in `fingroup.v`
  + definition `expgn_rec`, use `expgn` directly

- in `polydiv.v`
  + definition `gcdp_rec`, use `gcdp` directly

- in `nilpotent.v`
  + definition `lower_central_at_rec`, use `lower_central_at` directly
  + definition `upper_central_at_rec`, use `upper_central_at` directly

- in `commutator.v`
  + definition `derived_at_rec`, use `derived_at` directly

### Deprecated

- in `ssreflect.v`
  + notation `nosimpl` since `Arguments def : simpl never`
    does the job with Coq >= 8.18

- in `ssrfun.v`
  + notation scope `fun_scope`, use `function_scope` instead

- in `vector.v`
  + notation `vector_axiom`, use `Vector.axiom` instead

- in `ssrnat.v`
  + definition `addn_rec`, use `addn` directly
  + definition `subn_rec`, use `subn` directly
  + definition `muln_rec`, use `muln` directly
  + definition `expn_rec`, use `expn` directly
  + definition `fact_rec`, use `factorial` directly
  + definition `double_rec`, use `double` directly

### Infrastructure

### Misc

