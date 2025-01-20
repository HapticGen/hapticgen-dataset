# Publication
Youjin Sung, Kevin John, Sang Ho Yoon, and Hasti Seifi. 2025. Haptic-Gen: Generative Text-to-Vibration Model for Streamlining Haptic Design. In Proceedings of Proceedings of the CHI Conference on Human Factors in Computing Systems (CHI '25). ACM, New York, NY, USA, 21 pages. https://doi.org/3706598.3713609

# Field Descriptions
- `filename`: The name of the haptic signal .wav file generated for the user.
- `user_prompt`: The original natural language description of the tactile sensation provided by the user.
- `model`: The model used to generate the signal. The possible models include:
	"HapticGen": The final, fine-tuned model.
	"Baseline-AudioGen": A baseline model for A/B testing.
	"Initial": An early version of the HapticGen model without fine-tuning.
- `vote`: User feedback on the quality of the generated signal, where 1 indicates positive feedback (thumbs up), and -1 indicates negative feedback (thumbs down).
- `prompt_variant`: (Optional) A variant of the original prompt provided to the model for generating variations. This was not shown to users (not considered for vote).



# Schema
```ts
interface Metadata {
  /** The name of the corresponding .wav file. */
  filename: string;

  /** The natural language prompt provided by the user, describing the desired tactile sensation. */
  user_prompt: string;

  /**
   * The model used to generate the vibrotactile signal.
   * Possible values:
   * - "HapticGen": Final fine-tuned generative model.
   * - "Baseline-AudioGen": Baseline audio generation model for A/B comparison.
   * - "HapticGen-Initial": Early version of the HapticGen model (not fine-tuned, no normalization, ...)
   */
  model: "HapticGen" | "Baseline-AudioGen" | "HapticGen-Initial";

  /**
   * User feedback on the generated signal.
   * Possible values:
   * - 1: Positive feedback (thumbs up).
   * - -1: Negative feedback (thumbs down).
   */
  vote: 1 | -1;

  /**
   * (Optional) A variant of the original user prompt given to the model.
   * Used to create greater variations in the model output, but is not shown to the user.
   */
  prompt_variant?: string;
}
```
