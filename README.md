# marca-de-tinta
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { motion } from "framer-motion";
import { ScrollArea } from "@/components/ui/scroll-area";
import { Button } from "@/components/ui/button";
import Image from "next/image";

const completedBooks = [
  {
    id: 1,
    title: "Binding 13",
    cover: "/binding13.jpg",
    dateFinished: "2025-04-08",
    favoriteQuote: "You're safe here, Shannon.",
    keyMoments: ["Primer entrenamiento con Johnny", "Confesión en la biblioteca"],
    emotions: ["Emoción", "Tristeza", "Esperanza"],
    favoriteCharacter: "Johnny Kavanagh",
    symbolicImage: "/symbolic-binding13.png",
    magicStars: 5,
  },
  // Puedes agregar más libros aquí...
];

export default function RitualesDePapel() {
  const [selectedBook, setSelectedBook] = useState(null);

  return (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      className="p-4 space-y-4"
    >
      <h1 className="text-3xl font-bold text-center text-purple-700">
        Rituales de Papel
      </h1>

      {!selectedBook ? (
        <ScrollArea className="h-[70vh]">
          <div className="grid grid-cols-2 gap-4">
            {completedBooks.map((book) => (
              <motion.div
                whileHover={{ scale: 1.05 }}
                key={book.id}
                className="cursor-pointer"
                onClick={() => setSelectedBook(book)}
              >
                <Card>
                  <CardContent className="flex justify-center p-2">
                    <Image
                      src={book.cover}
                      alt={book.title}
                      width={120}
                      height={180}
                      className="rounded-xl shadow-lg"
                    />
                  </CardContent>
                </Card>
              </motion.div>
            ))}
          </div>
        </ScrollArea>
      ) : (
        <motion.div
          initial={{ x: 100, opacity: 0 }}
          animate={{ x: 0, opacity: 1 }}
          className="space-y-4"
        >
          <h2 className="text-2xl font-semibold text-indigo-600">
            {selectedBook.title}
          </h2>
          <p className="text-sm text-gray-500">
            Terminado el: {selectedBook.dateFinished}
          </p>
          <p>
            <span className="font-semibold">Frase favorita:</span>{" "}
            "{selectedBook.favoriteQuote}"
          </p>
          <p>
            <span className="font-semibold">Momentos clave:</span>{" "}
            {selectedBook.keyMoments.join(", ")}
          </p>
          <p>
            <span className="font-semibold">Emociones sentidas:</span>{" "}
            {selectedBook.emotions.join(", ")}
          </p>
          <p>
            <span className="font-semibold">Personaje favorito:</span>{" "}
            {selectedBook.favoriteCharacter}
          </p>
          <div className="flex items-center space-x-2">
            <span className="font-semibold">Estrellitas mágicas:</span>
            {[...Array(selectedBook.magicStars)].map((_, i) => (
              <span key={i}>✨</span>
            ))}
          </div>
          <div>
            <Image
              src={selectedBook.symbolicImage}
              alt="Imagen simbólica"
              width={200}
              height={200}
              className="rounded-xl shadow-md"
            />
          </div>
          <Button variant="outline" onClick={() => setSelectedBook(null)}>
            Volver
          </Button>
        </motion.div>
      )}
    </motion.div>
  );
}
import { useState } from "react";
import Image from "next/image";
import { motion } from "framer-motion";

const booksRead = [
  {
    id: 1,
    title: "Binding 13",
    cover: "/binding13.jpg",
    favorite: true,
  },
  {
    id: 2,
    title: "Keeping 13",
    cover: "/keeping13.jpg",
    favorite: false,
  },
  // Agrega más libros aquí
];

export default function EstanteriaMagica() {
  const [selectedBook, setSelectedBook] = useState(null);

  return (
    <div className="p-4">
      <h2 className="text-3xl font-bold text-center mb-6 text-purple-600">Estantería Mágica</h2>
      <div className="grid grid-cols-3 gap-4">
        {booksRead.map((book) => (
          <motion.div
            whileHover={{ scale: 1.05 }}
            key={book.id}
            className="relative cursor-pointer"
            onClick={() => setSelectedBook(book)}
          >
            <Image
              src={book.cover}
              alt={book.title}
              width={120}
              height={180}
              className="rounded-lg shadow-lg"
            />
            {book.favorite && (
              <span className="absolute top-1 right-1 text-yellow-400 text-lg">✨</span>
            )}
          </motion.div>
        ))}
      </div>

      {selectedBook && (
        <div className="mt-6 text-center">
          <p className="text-xl">Has seleccionado: <strong>{selectedBook.title}</strong></p>
        </div>
      )}
    </div>
  );
}
import { useState } from "react";
import Image from "next/image";

const outfits = [
  {
    id: 1,
    name: "Vestido Élfico",
    image: "/elfico.png",
    mood: "Misterioso y tranquilo",
  },
  {
    id: 2,
    name: "Capa Encantada",
    image: "/capa.png",
    mood: "Valiente y aventurera",
  },
  {
    id: 3,
    name: "Corona de flores",
    image: "/corona.png",
    mood: "Soñadora y alegre",
  },
  // Puedes seguir agregando...
];

export default function ProbadorMagico() {
  const [outfit, setOutfit] = useState(null);

  return (
    <div className="p-4 text-center">
      <h2 className="text-3xl font-bold text-pink-600 mb-4">Probador Mágico</h2>
      <div className="grid grid-cols-3 gap-4 mb-6">
        {outfits.map((item) => (
          <div
            key={item.id}
            className="cursor-pointer"
            onClick={() => setOutfit(item)}
          >
            <Image
              src={item.image}
              alt={item.name}
              width={80}
              height={80}
              className="rounded-full border border-purple-300 shadow-md"
            />
            <p className="mt-2 text-sm">{item.name}</p>
          </div>
        ))}
      </div>

      {outfit && (
        <div className="mt-6">
          <h3 className="text-xl font-semibold">{outfit.name}</h3>
          <p className="italic text-gray-500 mb-4">Estado de ánimo: {outfit.mood}</p>
          <Image
            src={outfit.image}
            alt={outfit.name}
            width={150}
            height={150}
            className="mx-auto rounded-xl shadow-lg"
          />
        </div>
      )}
    </div>
  );
}
import { useState } from "react";
import Image from "next/image";

const outfits = [
  {
    id: 1,
    name: "Vestido Élfico",
    image: "/elfico.png",
    mood: "Misterioso y tranquilo",
  },
  {
    id: 2,
    name: "Capa Encantada",
    image: "/capa.png",
    mood: "Valiente y aventurera",
  },
  {
    id: 3,
    name: "Corona de flores",
    image: "/corona.png",
    mood: "Soñadora y alegre",
  },
];

export default function ProbadorMagico() {
  const [outfit, setOutfit] = useState(null);

  return (
    <div className="p-4 text-center">
      <h2 className="text-3xl font-bold text-pink-600 mb-4">Probador Mágico</h2>
      <div className="grid grid-cols-3 gap-4 mb-6">
        {outfits.map((item) => (
          <div
            key={item.id}
            className="cursor-pointer"
            onClick={() => setOutfit(item)}
          >
            <Image
              src={item.image}
              alt={item.name}
              width={80}
              height={80}
              className="rounded-full border border-purple-300 shadow-md"
            />
            <p className="mt-2 text-sm">{item.name}</p>
          </div>
        ))}
      </div>

      {outfit && (
        <div className="mt-6">
          <h3 className="text-xl font-semibold">{outfit.name}</h3>
          <p className="italic text-gray-500 mb-4">Estado de ánimo: {outfit.mood}</p>
          <Image
            src={outfit.image}
            alt={outfit.name}
            width={150}
            height={150}
            className="mx-auto rounded-xl shadow-lg"
          />
        </div>
      )}
    </div>
  );
}
