---
title: Every Door FAQ
---
# Frequently Asked Questions

## Why the map is so tiny?

Because it's not the point. You only check your positioning on the map,
and pan it to adjust. Watch the amenity list below, sorted by distance
from you.

The map gets bigger when you edit amenities far from your location.
Although the app was made to edit things you see with your eyes.

## What are the checkmarks for?

These are marks that amenity data was confirmed. They add the
`check_date` tag with the current date.

The idea behind the checkmarks is that, say, you surveyed half
the city the first time. Then after a month you came back and
went to survey again. You need to somehow mark that you see
the amenity, but nothing has changed about it. That's the checkmark:
you tap it and continue.

The mark stays checked for two weeks. After that you may survey
the amenities again.

## How to add a building entrance?

At the top right there's a grey button for switching editing modes.
It changes modes between amenities, micromapping, and entrances.

In the entrance mode, tap or drag the door button in the bottom
right corner onto the map.

## Can I type letters into an apartment number?

If your numeric keyboard cannot be switched to a full one, check
the app settings. They are behind the button at the top left corner.
Switch on the "extended numeric keyboard" there.

## Are floors "3" and "/3" the same?

No. The first one has `addr:floor=3` tag filled. That's the floor
as it is printed on navigation and commonly used. The second one
does not have this tag, but has `level=3`. That number is a sequential
floor number from zero to `building:levels - 1`. That is, in a
three-storey building `addr:floor` value depends on a country,
but `level` is always 0, 1, or 2.

Here is how the notation in the editor related to these tags:

* `2`: `addr:floor=2` and non-empty `level=*`.
* `4/`: `addr:floor=4`, but there's no `level` tag.
* `/1`: `level=1`, but there's no `addr:floor` tag.
* `1/0`: `addr:floor=1` + `level=0` (and there's an object nearby
  with the same `addr:floor`, but different `level`, or vice-versa).

## Why is the street list missing some streets from the map?

Street names for editor fields are taken not from roads (`highway=*`),
but from the nearby addressed buildings and amenities (`addr:street=*`).
Therefore it might be impossible to set an address to a building
or an amenity, if there are no other addresses for the street.

This is an registered issue, follow [this ticket](https://github.com/Zverik/every_door/issues/61).

## How to change or translate preset fields?

The editor relies on iD editor presets. To modify these, submit
a pull request to [this repo](https://github.com/openstreetmap/id-tagging-schema).
Alas it's not maintained at the moment: we need to find volunteers
and convince the owners.

The presets are translated at [Transifex](https://www.transifex.com/openstreetmap/id-editor/translate/#ru/presets/).

To translate value options, first make a pull request to the repo
adding desired options, [like here](https://github.com/openstreetmap/id-tagging-schema/blob/main/data/fields/camera/type.json).
Then, when the translation source on Transifex is updated, there
will be strings to translate.
[Like here](https://www.transifex.com/openstreetmap/id-editor/translate/#ru/presets/101711314?q=key%3Apresets.fields.camera%2Ftype).