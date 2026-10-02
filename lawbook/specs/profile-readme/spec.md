# Profile README

### Requirement: Creator of SpecLaw placement

The profile README SHALL render a centered section titled "Creator of SpecLaw" after the hero and before the Flagship section.

#### Scenario: Heading sits between the hero and Flagship

- Given the profile README
- When the section headings are read in order
- Then "Creator of SpecLaw" appears after the hero and before "Flagship"

### Requirement: SpecLaw repository link

The Creator of SpecLaw section SHALL link the name SpecLaw to `https://github.com/esneiderbravo/speclaw`.

#### Scenario: SpecLaw points at the speclaw repository

- Given the Creator of SpecLaw section
- When the SpecLaw link is read
- Then its target is `https://github.com/esneiderbravo/speclaw`

### Requirement: Published tool name

The Creator of SpecLaw section SHALL name the published tool speclaw.

#### Scenario: Section text names speclaw

- Given the Creator of SpecLaw section
- When the section paragraph is read
- Then the paragraph contains the word speclaw

### Requirement: Brand badges

The Creator of SpecLaw section SHALL include shields for GitHub stars, the npm package, and the license, each using label color `0B0F10` and color `0E8E8E`.

#### Scenario: Three badges use the brand colors

- Given the Creator of SpecLaw section
- When the badge image URLs are read
- Then a stars shield, an npm shield, and a license shield are present
- And each URL includes `labelColor=0B0F10` and `color=0E8E8E`

### Requirement: Badge alt text

Every image in the Creator of SpecLaw section SHALL have non-empty alt text.

#### Scenario: Stars, npm, and license images are labeled

- Given the Creator of SpecLaw section
- When each image is read
- Then the stars image alt text is non-empty
- And the npm image alt text is non-empty
- And the license image alt text is non-empty

### Requirement: Disabled activity graph is absent

The profile README SHALL NOT embed `github-readme-activity-graph.vercel.app`.

#### Scenario: Dead activity-graph host is not referenced

- Given the profile README
- When image sources are read
- Then no image source contains `github-readme-activity-graph.vercel.app`

### Requirement: Contribution calendar remains

The profile README SHALL keep the contribution calendar image.

#### Scenario: Calendar image is still present

- Given the profile README
- When image alt text is read
- Then an image with alt text "Contribution calendar" is present

### Requirement: Neighbor sections remain

The profile README SHALL keep the Flagship, Selected work, and GitHub in motion sections after the Creator of SpecLaw section.

#### Scenario: Later headings stay in order

- Given the profile README after the creator section is added
- When the section headings are read in order
- Then the headings are "Creator of SpecLaw", "Flagship", "Selected work", and "GitHub in motion"
