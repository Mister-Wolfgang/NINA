# Analysis Patterns - Prompt Optimization Detection

## Structural Analysis Patterns

### ✅ Verbosity Detection
```
INDICATORS:
- Repetitive phrases: "il est important de", "il faut que", "nous devons"
- Redundant explanations: Same concept explained multiple times
- Unnecessary qualifiers: "très", "vraiment", "particulièrement"
- Long connector phrases: "en d'autres termes", "par conséquent"

MEASUREMENT:
- Token density: Meaning per token ratio
- Redundancy ratio: Repeated concepts/total concepts
- Connector overhead: Linking words/content words
```

### ✅ Structure Inefficiency Detection
```
INDICATORS:
- Missing P.R.I.M.A. structure
- Scattered instructions without logical flow
- Embedded long lists that could be externalized
- Mixed abstraction levels in same section

MEASUREMENT:
- Structure clarity score: 1-10 scale
- Instruction density: Actions per paragraph
- Modularity potential: Extractable components count
```

### ✅ Ambiguity Detection
```
INDICATORS:
- Vague action verbs: "gérer", "traiter", "s'occuper de"
- Multiple interpretation paths
- Missing context or constraints
- Unclear success criteria

MEASUREMENT:
- Precision score: Specific instructions/total instructions
- Context completeness: Required context provided
- Action clarity: Executable vs interpretable instructions
```

## Content Analysis Patterns

### ✅ Expertise Integration Analysis
```
CHECK FOR:
- Domain knowledge embedded
- Industry standards referenced
- Best practices included
- Expert-level terminology used

GAPS IDENTIFIED:
- Generic advice without specialization
- Missing authoritative references
- Beginner-level explanations for expert audience
- Lack of proven methodologies
```

### ✅ Audience Alignment Analysis
```
EVALUATE:
- Language complexity appropriate for target
- Examples relevant to audience context
- Assumptions match audience expertise
- Output format fits audience needs

MISALIGNMENTS:
- Over-simplification for expert audience
- Technical jargon for general audience
- Irrelevant examples or contexts
- Wrong abstraction level
```

## Optimization Opportunity Detection

### ✅ Compression Potential Identification
```
HIGH COMPRESSION OPPORTUNITIES:
- Long descriptive phrases → compact notation
- Embedded lists → external references
- Repetitive structures → templates
- Verbose instructions → symbolic notation

MEDIUM COMPRESSION:
- Standard phrases → acronyms
- Common patterns → shortcuts
- Related concepts → grouped notation

LOW COMPRESSION:
- Critical unique instructions
- Domain-specific requirements
- Personality/tone elements
```

### ✅ Modularization Opportunities
```
EXTRACT TO REFERENCES:
- Configuration options (>50 tokens)
- Detailed examples (>100 tokens)
- Rules and constraints lists
- Standards and methodologies

KEEP INLINE:
- Core workflow logic
- Critical success criteria
- Personality elements
- Brief contextual examples
```

## Quality Preservation Analysis

### ✅ Critical Element Identification
```
MUST PRESERVE:
- Business logic workflows
- Quality standards and criteria
- Unique personality elements
- Domain expertise requirements
- Essential constraints and rules

MEASUREMENT:
- Logic complexity score
- Business rule density
- Unique value proposition elements
- Critical constraint count
```

### ✅ Enhancement Opportunities
```
IMPROVE WHILE OPTIMIZING:
- Structure clarity: Better organization
- Flow logic: Clearer sequences
- Instruction precision: More specific actions
- Validation completeness: Better success criteria

ENHANCEMENT METRICS:
- Clarity improvement potential
- Structure optimization score
- Precision enhancement opportunities
- Validation gap identification
```

## Anti-Pattern Detection

### ❌ Over-Optimization Risks
```
WARNING SIGNS:
- Removing critical context
- Compressing unique personality
- Eliminating domain expertise
- Breaking logical dependencies

PREVENTION:
- Preserve all business rules
- Maintain expert-level content
- Keep essential examples
- Validate functionality integrity
```

### ❌ Under-Optimization Indicators
```
MISSED OPPORTUNITIES:
- <50% token reduction achieved
- No modular extraction performed
- Verbose syntax still present
- No structural improvements

TARGETS:
- Aim for 70-90% token reduction
- Extract 3+ reference modules
- Apply compact syntax consistently
- Improve structural clarity
```
