#Импортируем необходимые библиотеки
import cv2
from noti_bot import send_notification
import time
#Создаём функцию для захвата изображения с веб-камеры
def face_capture():
    cascade_path = 'filter/haarcascade_frontalface_default.xml'

    clf = cv2.CascadeClassifier(cascade_path)
    camera = cv2.VideoCapture(0)
    #Задаём параметры обработки входящего видео-потока для облегчения распознования ИИ
    while True:
        _, frame = camera.read()
        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

        faces = clf.detectMultiScale(
            gray,
            scaleFactor=1.1,
            minNeighbors=5,
            minSize=(30, 30),
            flags=cv2.CASCADE_SCALE_IMAGE,

        )

        for(x, y, width, height) in faces:
            cv2.rectangle(frame, (x, y), (x + width, y + height), (255, 255, 0), 2)



        cv2.imshow('Faces', frame)
        #Составляем список популярных клавиш, после нажатия которых будет отправлено сообщение
        if cv2.waitKey(1) == ord('c'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
        if cv2.waitKey(1) == ord('h'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
        if cv2.waitKey(1) == ord('d'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
        if cv2.waitKey(1) == ord('a'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
        if cv2.waitKey(1) == ord('y'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
	if cv2.waitKey(1) == ord('o'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
	if cv2.waitKey(1) == ord('b'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
	if cv2.waitKey(1) == ord('j'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)
	if cv2.waitKey(1) == ord('l'):
            message = ("Кто-то попался в поле зрения камеры!")
            send_notification(message)


        if cv2.waitKey(1) == ord('f'):
            break
    #Функциии для выхода из приложения
    camera.release()
    cv2.destroyAllWindows()



def main():
    face_capture()

if __name__ == '__main__':
    main()






#Импортируем необходимые библиотеки для работы телеграм-бота
from notifiers import get_notifier
import time
#Подключаем телеграм-бота
token = '6745541432:AAH_l5IQCroYAv0_WKp0MbGr6MgIiMOw_tw'
chat_id = '403904403'
#Создаём функцию для отправки сообщений
def send_notification(message):
    telegram = get_notifier('telegram')
    message_text = message
    telegram.notify(token=token, chat_id=chat_id, message=message_text)

if __name__ == "__main__":

    while True:
        message = ("Кто-то попался в поле зрения камеры!")
        time.sleep(60)
        send_notification(message)
