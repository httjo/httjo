- 👋 Hi, I’m @httjo
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
httjo/httjo is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import { useState, useEffect } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Button } from "@/components/ui/button"; import { Input } from "@/components/ui/input";

const exercises = { Monday: "Cuestiona una creencia personal. Elige algo que siempre hayas creído y analiza sus fundamentos.", Tuesday: "Detecta falacias. Mira un video o lee algo y encuentra errores lógicos o trampas emocionales.", Wednesday: "Debate contigo mismo. Defiende un tema desde dos puntos de vista opuestos.", Thursday: "Analiza una decisión. Evalúa cómo decidiste algo esta semana y si fue racional o emocional.", Friday: "Lee y reflexiona. Resume un texto y cuestiona su estructura y argumentos.", Saturday: "Juego mental. Juega ajedrez, sudoku o un juego de lógica y analiza tus decisiones.", Sunday: "Dilema ético. Imagina un dilema difícil y analiza opciones, consecuencias y valores." };

const getTodayExercise = () => { const day = new Date().toLocaleDateString("en-US", { weekday: "long" }); return exercises[day]; };

export default function MenteCriticaApp() { const [response, setResponse] = useState(""); const [saved, setSaved] = useState(false);

const handleSave = () => { localStorage.setItem("menteCritica_" + new Date().toDateString(), response); setSaved(true); setTimeout(() => setSaved(false), 2000); };

const exercise = getTodayExercise();

return ( <div className="max-w-xl mx-auto mt-10 p-4"> <h1 className="text-3xl font-bold mb-4 text-center">Mente Crítica</h1> <Card> <CardContent className="p-4"> <h2 className="text-xl font-semibold mb-2">Ejercicio del día</h2> <p className="mb-4">{exercise}</p> <textarea className="w-full p-2 border rounded mb-4" rows={6} placeholder="Escribe tu reflexión aquí..." value={response} onChange={(e) => setResponse(e.target.value)} ></textarea> <Button onClick={handleSave}>Guardar reflexión</Button> {saved && <p className="mt-2 text-green-600">¡Reflexión guardada!</p>} </CardContent> </Card> </div> ); }


